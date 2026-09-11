# Packer Lab
This repository contains packer related content like packer files and other documents to implement images as a code.

## Prerequisites
Below prerequisites must be fulfilled for successful execution of code.

### Software Requirement
Resources in this repository are meant for use with Packer (check the version using `packer version`). If you don't have the compatible version, install it from official packer documentation. See [Installation-Guide](./docs/install.md) on how to install Packer.

- [packer](https://developer.hashicorp.com/packer/downloads) >= 1.8.5

### Permissions
Authenticating with Google Cloud services requires either a User Application Default Credentials, a JSON Service Account Key or an Access Token. These are not required if you are running the googlecompute Packer builder on Google Cloud with a properly-configured Google Service Account.

1. If you run the googlecompute Packer builder locally on your workstation, you will need to install the Google Cloud SDK and authenticate using User Application Default Credentials. You don't need to specify an account file if you are using this method. Your user must have at least below roles to use Packer succesfully.

- Compute Instance Admin (v1)
- Service Account User roles

2. Make sure to open your firewall to allow ssh connection to virtual machine launched by packer for building image.

## Execution
To execute the packer commands for building the image, go to command prompt and switch to the directory conatinaing all the packer config files and run the following commands:

-   [Required] `packer init`
-   [Optional] `packer fmt .`
-   [Optional] `packer validate .`
-   [Required] `packer build .`

**Note:** See [Packer-Guide](./docs/info.md) to get real-quick overview of Packer.

## Run pre-commit
The pre-commit framework is a powerful, language-agnostic tool for managing Git hooks. Create a .pre-commit-config.yaml file in the root of your repository. Run the below commnad from the git repo root to set up the git hook scripts into your git hooks. It will be installed at .git/hooks/pre-commit

```bash
pre-commit install
pre-commit install --config <file> # If config file has non-standard name
pre-commit validate-config # Validate .pre-commit-config.yaml files
```

now pre-commit will run automatically on git commit. Usually, it runs only for the changed files. Its good to run the hooks against all the files when adding new hooks. To manually run all pre-commit hooks on a repo, use below -

```bash
# to run hooks on all files
pre-commit run --all-files

# to run hooks on all files using a non-standard naming config file
pre-commit run --all-files --config .pre-commit-config-old.yaml

# to run individual hook
pre-commit run <hook_id>
```

Once you have pre-commit installed, adding pre-commit plugins to your project is done with the .pre-commit-config.yaml configuration file. You can generate a very basic configuration using `pre-commit sample-config`. Every time you clone a project using pre-commit running pre-commit install should always be the first thing you do.

## Contributing

Contributions are welcome! Please open issues or submit pull requests for improvements or new suggestions. Read the [contributing.md](CONTRIBUTING.md) before starting.

## References
- https://developer.hashicorp.com/packer/docs
- https://developer.hashicorp.com/packer/plugins/builders/googlecompute