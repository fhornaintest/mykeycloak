# Keycloak Example

### Here is the procedure to deploy and run the demo :

```
git clone https://github.com/fhornaintest/mykeycloak.git
podman login https://quay.io
podman run --name keycloak -e KC_BOOTSTRAP_ADMIN_USERNAME=admin -e KC_BOOTSTRAP_ADMIN_PASSWORD=admin -p 8180:8080 quay.io/keycloak/keycloak:latest start-dev
chmod 755 ./mykeycloak/mvnw
./mykeycloak/mvnw package
jar -jar mykeycloak/target/quarkus-app/quarkus-run.jar
```
You should be able to access your Keycloak Server at [localhost:8180/auth](http://localhost:8180/auth).

Log in as the `admin` user to access the Keycloak Administration Console.
Username should be `admin` and password `admin`.

Import the [realm configuration file](config/quarkus-realm.json) to create a new realm.
For more details, see the Keycloak documentation about how to [create a new realm](https://www.keycloak.org/docs/latest/server_admin/index.html#_create-realm).

1. Visit the default endpoint: [http://127.0.0.1:8080](http://127.0.0.1:8080).
    - You should be redirected to the login page at Keycloak

2. Authenticate as user `alice`
    - Username: `alice`
    - Password: `alice`

3. If the credentials you provided are valid and you were successfully authenticated, you should be redirected back to the application

4. You should be able to access now the `index.html` resource.

5. Visit the `/tokens` endpoint: [http://127.0.0.1:8080/tokens](http://127.0.0.1:8080/tokens).
    - You should have access to a HTML page that shows information based on the ID Token, Access Token and Refresh Token issued
    to the application. Where these tokens are available for injection as you can see in the `TokenResource` JAX-RS Resource.
