# Keycloak Example

### Here is the procedure to deploy and run the demo :

```
git clone
podman login https://quay.io
podman run --name keycloak -e KC_BOOTSTRAP_ADMIN_USERNAME=admin -e KC_BOOTSTRAP_ADMIN_PASSWORD=admin -p 8180:8080 quay.io/keycloak/keycloak:latest start-dev
./mykeycloak/mvnw package
jar -jar mykeycloak/target/quarkus-app/quarkus-run.jar
```
