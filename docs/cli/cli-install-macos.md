# Install krateo on macOS

The following methods exist for installing krateo on macOS:

- [Install krateo binary with curl on macOS](#install-krateo-binary-with-curl-on-macos)
- [Install with Homebrew on macOS](#install-with-homebrew-on-macos)

## Install krateo binary with curl on macOS

Step 1. Download the latest release with the command:

=== "Intel"

    ```sh
    curl -LO https://github.com/krateoplatformops/krateo/releases/download/v1.3.5/krateo_1.3.5_darwin_amd64.tar.gz
    ```

    !!! note

        - to download a specific version, replace the {VERSION} with your desired release 
        
        ```
        curl -LO https://github.com/krateoplatformops/krateo/releases/download/v{VERSION}/krateo_{VERSION}_darwin_amd64.tar.gz
        ```

=== "Apple Silicon"

    ```sh
    curl -LO https://github.com/krateoplatformops/krateo/releases/download/v1.3.5/krateo_1.3.5_darwin_arm64.tar.gz
    ```

    !!! note

        - to download a specific version, replace the {VERSION} with your desired release 
        
        ```
        curl -LO https://github.com/krateoplatformops/krateo/releases/download/v{VERSION}/krateo_{VERSION}_darwin_arm64.tar.gz
        ```

Step 2. Extract the tar.gz archive

```sh
tar -xf krateo_1.3.5_linux_amd64.tar.gz
```

Step 3. Install krateo to the `~/.local/bin` directory:

```sh
chmod +x krateo
mkdir -p ~/.local/bin
mv ./krateo ~/.local/bin/krateo
# and then append (or prepend) ~/.local/bin to $PATH
```

Step 4. Test to ensure the version you installed is up-to-date

```sh
krateo version
```

## Install with Homebrew on macOS

If you are on macOS and using [Homebrew](https://docs.brew.sh) package manager, krateo is available for installation.

```sh
brew install krateo
krateo version
```