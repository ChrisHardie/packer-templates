# Packer templates for deploying Laravel apps on Digital Ocean

These are my [Packer](https://www.packer.io) templates for deploying Laravel applications on Digital Ocean infrastructure.

Installs:

* PHP 8
* Nginx
* MySQL
* Redis
* Memcached
* Postfix
* Certbot
* Supervisor

## Configuration

Create a `variables.json` file with your [Digital Ocean API token](https://cloud.digitalocean.com/account/api/tokens):

```json
{
  "do_api_token": "YOUR_DIGITAL_OCEAN_API_TOKEN_HERE"
}
```

## Usage

To build a Digital Ocean droplet snapshot in `nyc3`:

```shell
brew upgrade packer
packer plugins install github.com/digitalocean/digitalocean
packer validate -var-file=variables.json laravel-lemp/template.json
packer build -var-file=variables.json laravel-lemp/template.json
```

Then, [create a droplet from the resulting snapshot](https://docs.digitalocean.com/products/images/snapshots/how-to/create-and-restore-droplets/).

## More information

Links and guides that helped inform this setup:

* [How To Create DigitalOcean Snapshots Using Packer on Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-create-digitalocean-snapshots-using-packer-on-ubuntu-16-04#troubleshooting)
* [1-Click Droplet Packer Build templates](https://github.com/digitalocean/droplet-1-clicks)
* [Digital Ocean Packer builder plugin](https://www.packer.io/plugins/builders/digitalocean)

## Author

[Chris Hardie](https://chrishardie.com/)