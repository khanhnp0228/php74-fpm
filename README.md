# php74-fpm Docker Env

## XDebug Support

Disable `utw` then restart

```
sudo utw disable
```

### VSCODE config 

```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for Xdebug",
            "type": "php",
            "request": "launch",
            "port": 9003,
            "pathMappings": {
                "/var/www/html": "${workspaceRoot}/src"
            }
        },
    ]
}
```

## WP-CLI Support

### WP-CLI: BASIC

This docker env does support wp-cli also

```
docker-compose run --rm wpcli WPCLI_COMMANDS
docker-compose run --rm wpcli --path=`path/to/wordpress` WPCLI_COMMANDS
```

### WP-CLI: DOWNLOAD WORDPRESS SOURCECODE

```
docker-compose run --rm wpcli core download --version=[WP_VERSION] --path=[PROJECT_NAME]
```

### WP-CLI: CREATE CONFIG FILE (wp-config.php)

```
docker-compose run --rm wpcli config create --path=[PROJECT_NAME] --dbprefix=[TABLE_PREFIX] --dbname=[DB_NAME] --dbuser=root --dbpass=root --dbhost=mariadb
```

### WP-CLI: CREATE DB

```
docker-compose run --rm wpcli db create --path=[PROJECT_NAME]
```

### WP-CLI: HASH PASSWORD

```
docker-compose run --rm wpcli eval "echo wp_hash_password('[CLEAR_PASSWORD]');" --path=[PROJECT_NAME]
```

### WP-CLI: CREATE USER WITH [CLEAR_PASSWORD]

```
docker-compose run --rm wpcli user create [USERNAME] [YOUR_EMAIL] --role=administrator --user_pass=[CLEAR_PASSWORD] --path=[PROJECT_NAME]
```

### WP-CLI: CREATE USER WITH PASSWORD GENERATE

```
docker-compose run --rm wpcli user create [USERNAME] [YOUR_EMAIL] --role=administrator --path=[PROJECT_NAME]
```

### WP-CLI: UPDATE USER PASSWORD

```
docker-compose run --rm wpcli user update [USERNAME] --user_pass=<CLEAR_PASSWORD> --path=[PROJECT_NAME]
```

### WP-CLI: SEARCH & REPLACE

```
docker-compose run --rm wpcli user search-replace '[OLD_STR]' '[NEW_STR]' --all-tables --path=[PROJECT_NAME]
```

### WP-CLI: SHOW EVENT LIST (WP Cron)

```
docker-compose run --rm wpcli cron event list --path=[PROJECT_NAME]
```

### WP-CLI: REGENERATE THUMBNAILS

```
docker-compose run -u 1000 --rm wpcli media regenerate --yes --path=[PROJECT_NAME]
```

### WP-CLI: EWWWIO OPTIMIZE

```
docker-compose run -u 1000 --rm wpcli ewwwio optimize media --noprompt --path=[PROJECT_NAME]
```