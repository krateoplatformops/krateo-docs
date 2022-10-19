# Install krateo on Linux

The following methods exist for installing krateo on Linux:

- [Install krateo binary with curl on Linux](#install-krateo-binary-with-curl-on-linux)
- [Install using other package management](#install-using-other-package-management)

## Install krateo binary with curl on Linux

Step 1. Download the latest release with the command:

```sh
curl -LO https://github.com/krateoplatformops/krateo/releases/download/v1.3.5/krateo_1.3.5_linux_amd64.tar.gz
```

!!! note

    - to download a specific version, replace the {VERSION} with your desired release 
    - to download a binary compiled for a arm architecture, replace {ARCH} with `arm64`

    ```
    curl -LO https://github.com/krateoplatformops/krateo/releases/download/v{VERSION}/krateo_{VERSION}_linux_{ARCH}.tar.gz
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

## Install using other package management

=== "Homebrew"

    If you are on Linux and using [Homebrew](https://docs.brew.sh/Homebrew-on-Linux) package manager, krateo is available for installation.

    ```sh
    brew install krateo
    krateo version
    ```