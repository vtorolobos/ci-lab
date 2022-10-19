# ci-lab
laboratorio de integración continua


# Parte 1: GitHub Actions

- Configura una action importando el plugin Maven, tal como lo mostró el profesor
- Modifica el archivo `maven-publish.yml` dejándolo así:

```
name: Maven Package

on: push

jobs:
  build:

    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write

    steps:
    - uses: actions/checkout@v3
    - name: Set up JDK 11
      uses: actions/setup-java@v3
      with:
        java-version: '11'
        distribution: 'temurin'
        server-id: github # Value of the distributionManagement/repository/id field of the pom.xml
        settings-path: ${{ github.workspace }} # location for the settings.xml file

    - name: Build with Maven
      run: mvn -B package --file pom.xml # or verify
```

- Luego reemplaza `package` por `verify`
- Crea un token clasic en tu configuración personal
- Crea los secrets USER y TOKEN en el repo
-
