# Install krateo on Windows

The following methods exist for installing krateo on Windows:

- [Install krateo binary with curl on Windows](#install-krateo-binary-with-curl-on-windows)


## Install krateo binary with curl on Windows

Step 1. [Download](https://github.com/krateoplatformops/krateo/releases/latest) the latest release.

  Or if you have curl installed, use this command:

```sh
curl -LO https://github.com/krateoplatformops/krateo/releases/download/v1.3.5/krateo_1.3.5_windows_amd64.tar.gz
```

!!! note

    - to download a specific version, replace the {VERSION} with your desired release 
    
    ```
    curl -LO https://github.com/krateoplatformops/krateo/releases/download/v{VERSION}/krateo_{VERSION}_windows_amd64.tar.gz
    ```

Step 2. Append or prepend the krateo binary folder to your `PATH` environment variable.

Step 3. Test to ensure the version you installed is up-to-date

```sh
krateo.exe version
```
