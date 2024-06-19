# GitHub Action - github-setup-gpg

Tis is a GitHub action preparing GPG for signing files without entering a password.

If successful, it stores the given password in the file, which is given in the input `password_file`.

If not successful, the latter file will no be existing.

## Example

```yaml
  steps:
    - uses: actions/checkout@v4

    - uses: fbrehm/prepare-debian-container@v1

    - uses: fbrehm/github-setup-gpg@main
      with:
        with:
          public_key: ${{ secrets.public_key }}
          private_key: ${{ secrets.private_key }}
          key_password: ${{ secrets.key_password }}
          password_file: ${{ inputs.password_file }}
          key_id: ${{ inputs.key_id }}
```

## Inputs

```yaml
inputs:
  public_key:
    description: "This is the exported public GPG key"
    required: true
  private_key:
    description: "This is the exported private GPG key"
    required: true
  key_password:
    description: "This is the password of the imported private GPG key"
    required: true
  password_file:
    description: "The file containing the password of the private GPG key."
    default: '.private/uhu.txt'
  key_id:
    description: "The ID of the private GPG key."
    required: true
```


