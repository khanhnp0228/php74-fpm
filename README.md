# php74-fpm Docker Env

## WP-CLI Supprot

### WP-CLI: BASIC

This docker env does support wp-cli also

```
docker-compose run --rm wpcli WPCLI_COMMANDS
docker-compose run --rm wpcli --path=`path/to/wordpress` WPCLI_COMMANDS
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


### WP-CLI: REGENERATE THUMBNAILS

```
docker-compose run -u 1000 --rm wpcli media regenerate --yes --path=[PROJECT_NAME]
```

### WP-CLI: EWWWIO OPTIMIZE

```
docker-compose run -u 1000 --rm wpcli ewwwio optimize media --noprompt --path=[PROJECT_NAME]
```