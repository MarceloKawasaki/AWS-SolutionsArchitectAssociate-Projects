# IIS Post-Migration Configuration

## Validate Application Pool Identity

Navigate:

```text
IIS → Application Pools
```

Review:

- Service account
- Permissions
- ApplicationPoolIdentity

Recycle application pools after changes.

---

# Validate Bindings

Navigate:

```text
IIS → Site → Bindings
```

Confirm:

- HTTP 80
- HTTPS 443
- Hostname bindings

---

# Load Balancer Integration

In many AWS environments:

```text
Client
    |
HTTPS 443
    |
Application Load Balancer
    |
HTTP 80
    |
IIS Server
```

SSL termination occurs at the Load Balancer.

---

# Update Multiple Application Pools

Example:

```powershell
Import-Module WebAdministration

$userName = "DOMAIN\\service_account"
$password = "<password>"

$appPools = Get-ChildItem IIS:\AppPools

foreach ($appPool in $appPools) {
    $appPoolName = $appPool.Name

    Set-ItemProperty "IIS:\AppPools\$appPoolName" -Name processModel.identityType -Value 3
    Set-ItemProperty "IIS:\AppPools\$appPoolName" -Name processModel.userName -Value $userName
    Set-ItemProperty "IIS:\AppPools\$appPoolName" -Name processModel.password -Value $password
}
```

---

# Update Multiple Applications

Example:

```powershell
Import-Module WebAdministration

$userName = "DOMAIN\\service_account"
$password = "<password>"

$sites = Get-Website

foreach ($site in $sites) {
    $applications = Get-WebApplication -Site $site.Name

    foreach ($app in $applications) {

        Set-WebConfigurationProperty `
        -pspath "MACHINE/WEBROOT/APPHOST" `
        -filter "system.applicationHost/sites/site[@name='$($site.Name)']/application[@path='$($app.Path)']/virtualDirectory[@path='/']" `
        -name "userName" `
        -value $userName

        Set-WebConfigurationProperty `
        -pspath "MACHINE/WEBROOT/APPHOST" `
        -filter "system.applicationHost/sites/site[@name='$($site.Name)']/application[@path='$($app.Path)']/virtualDirectory[@path='/']" `
        -name "password" `
        -value $password
    }
}
```

---

# Best Practices

- Use dedicated service accounts.
- Validate permissions before cutover.
- Keep SSL termination centralized whenever possible.
- Test all application endpoints after migration.
