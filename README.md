
- [DDEV](https://ddev.readthedocs.io/en/latest/)
- [Roots Sage Starter Theme](https://github.com/roots/sage)

🚧 Work in progress 🚧

## Setup for local development

```bash
ddev start
ddev wp core download

# Finish installation in browser:
ddev launch

# Install roots/acorn plugin (required)
# replace with latest link (https://github.com/roots/acorn/releases)
ddev wp plugin install https://github.com/roots/acorn/releases/download/v2.1.2/acorn-v2.1.2-php-8.0.zip --activate

# Jump into DDEV container to work in the sub-dir:
ddev ssh
cd wp-content/themes/my-sage-theme/
composer install
yarn install
exit

# Activate theme
ddev wp theme activate my-sage-theme
```

## Local development

```
ddev ssh
cd wp-content/themes/my-sage-theme/
yarn dev
```

Important: Open https://ddev-wp-sage.ddev.site:3000 in your browser for local dev.

## How was this created?

```bash
# https://ddev.readthedocs.io/en/stable/users/quickstart/#wp-cli
ddev config --project-type=wordpress
ddev start
ddev wp core download

# Finish install in browser:
ddev launch

# Sage theme by Roots
# https://docs.roots.io/sage/10.x/installation/

# Install roots/acorn plugin (required)
# replace with latest link (https://github.com/roots/acorn/releases)
ddev wp plugin install https://github.com/roots/acorn/releases/download/v2.1.2/acorn-v2.1.2-php-8.0.zip --activate
#ddev exec mkdir -p wp-content/mu-plugins && \
#    ddev exec wget -O wp-content/mu-plugins/acorn.zip https://github.com/roots/acorn/releases/download/v2.1.2/acorn-v2.1.2-php-8.0.zip && \
#    ddev exec 'cd wp-content/mu-plugins/ && unzip acorn.zip' && \
#    ddev exec rm wp-content/mu-plugins/acorn.zip

# We jump into DDEV container to use composer in a sub-dir
ddev ssh
cd wp-content/themes/
composer create-project roots/sage my-sage-theme
cd my-sage-theme/
yarn install

# Added custom .gitignore which only tracks child theme
```