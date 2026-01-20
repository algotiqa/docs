# Keycloak setup

## Starting Keycloak

You need to pull the `environment` repository and have both Podman and Podman compose packages installed. 
Once done, enter the `identity-provider` folder and run Podman:

```
cd identity-provider
sudo rm -rf database
mkdir database
podman compose up -d
```

## Importing the realm

Go to: https://algotiqa-server:8443/auth and login using the default credentials:
- Username: `keycloak-admin`
- Password: `key!cloak.2K`

Click the `Keycloak` dropdown and select `Create realm`. Click `Browse` and upload the `algotiqa-realm.json` inside the
`identity-provider` folder. Now, clicking `Create` the `algotiqa` realm will be created.

## Configuring users

### Creating a normal user

After login, select the `algotiqa` realm. We need to create an admin user (`admin`) and a generic user
(`user`). Click `Users` on the left and then the `Create new user` button. Use the following settings:

- Email verified = yes
- Username       = user
- First name     = User
- Last name      = User

Then, click `Create`. Now, on the user tab, click `Credentials` and then `Set password`. Use the following settings:
- Temporary = Off
- Password = `bf#user` (or any other password)

Click `Save` and then the `Save password` button.

Now, click `Role mapping`, then `Assign role` and select the `User` role.

### Creating an administrator

Use the same process described above to create the `admin` user. Use:
- Username   = admin
- First name = Admin
- Last name  = Admin
- Password   = `bf#admin` (or any other password)
- Role       = admin

### Configure service account

The role must be set to "service"
The client secret must be regenerated

