# wkhtmltopdf Buildpack

This is a [Heroku buildpack][0] for bundling a compatible [wkhtmltopdf][1] binary with your environment.

Loosely based on [dscout/wkhtmltopdf-buildpack](https://github.com/dscout/wkhtmltopdf-buildpack).

## Versions

* Buildpack:   `1.0`
* wkhtmltopdf: `0.11.0_rc1` (default version)
  - Set heroku env variables to use a different version.

    Example:
    ```bash
    heroku config:set WKHTMLTOPDF_FILENAME="wkhtmltopdf-0.11.0_rc1-static-amd64.tar.bz2"
    heroku config:set WKHTMLTOPDF_URL="http://download.gna.org/wkhtmltopdf/obsolete/linux"
    heroku config:set WKHTMLTOPDF_DOWNLOAD_SHA="b20c17284d4c03d81ac6ec3e251201da2b99830c9ac831281c8b5d841e7a6632"
    ```

## Usage

This buildpack only installs wkhtmltopdf, it isn't very useful by itself. You'll probably want to use it as part of a multi-buildpack. Here is an example using the Ruby buildpack.

```bash
$ heroku buildpacks:set 'https://github.com/heroku/heroku-buildpack-multi.git'
$ echo 'https://github.com/heroku/heroku-buildpack-ruby.git' >> .buildpacks
$ echo 'https://github.com/barsoom/wkhtmltopdf-buildpack.git' >> .buildpacks
$ git add .buildpacks
$ git commit -m 'Add multi-buildpack'
```

[0]: http://devcenter.heroku.com/articles/buildpacks
[1]: http://wkhtmltopdf.org/

## Troubleshooting

If you run into issues when trying to deploy with this buildpack, make sure your app is running on Cedar with Ubuntu 14.04 (`cedar-14`). You can check this with:

```bash
$ heroku stack
```

If you are on an older stack, you can upgrade to `cedar-14` with:

```bash
$ heroku stack:set cedar-14
```
