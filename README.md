Bring up containers
===
`docker-compose up -d --build`

Installing Drupal
===
`docker exec -it drupal_1 bash`
`/app #  composer create-project drupal-composer/drupal-project:8.x-dev /app --stability dev --no-interaction`
`/app #  mkdir -p /app/config/sync
`/app #  chown -R www-data:www-data /app/web`
`/app #  drush config-export`
`/app #  exit`

Shell login
===
`docker exec -it drupal_1 bash`

Updating Drupal 8 Core
====
`git checkout -b update-drupal`

`docker exec -it drupal bash`

`/app #composer update drupal/core --with-dependencies`

`/app #drush updb`

`/app #  exit`

`git add .`

`git commit -m "Updated Drupal Core."`

`git push`


Installing a “Contrib” Module or Theme
==
`git checkout -b install-pathauto`

`docker exec -it drupal_1 bash`

`/app #composer require drupal/pathauto`

`/app #drush en pathauto -y`

`/app #  exit`

`git add .`

`git commit -m "Installed Pathauto."`

`git push`

Updating Drupal “Contrib” Modules & Themes
====

`git checkout -b update-pathauto`

`docker exec -it drupal_1 bash`

`/app #  composer update drupal/pathauto --with-dependencies`

`/app #  drush updb  # updates the DB with any schema changes`

`/app #  exit`

`git add .`

`git commit -m "Updated Pathauto."`

`git push`