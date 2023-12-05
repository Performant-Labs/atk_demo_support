## INTRODUCTION

The ATK Demo Support module provides content and configuration
to run Automated Testing Kit tests. USE THE ATK_DEMO RECIPE BELOW TO INSTALL
THIS MODULE and read the project documentation for further configuration guidance.

See the project documentation at 
https://performantlabs.com/automated-testing-kit/automated-testing-kit

## REQUIREMENTS

The following modules are required by this module:
- Admin Toolbar (provide dropdown menus in toolbar)
- Admin Toolbar Tools (add functionality to toolbar)
- Automated Testing Kit (contains the tests of Automated Testing Kit)
- Default Content (installs a 404 page and welcome page)
- Gin (well-designed admin theme)
- Gin Login (well-designed login page)
- Gin Toolbar (allows the Gin toolbar to be visible in other themes)
- Pathauto (allow URL aliases)
- QA Accounts (create accounts just for QA team)
- Redirect (URL Redirection)
- Symfony Mailer (mail transfer agent to send email to Ethereal)
- Token (provide system-wide tokens)
- Webform (provide Contact Us form)
- XML Sitemap (provide site map)
  
## INSTALLATION

Create and configure an empty, Drupal 10+ site then use the atk_demo
recipe to install this module.

NOTE: Installing the demo module via Composer will not set up necessary configuration. 
Use the recipe instructions below. Once Recipes are in core, most of these steps will
be unnecessary.

Follow these instructions:
1. Change the directory names as needed:
   cd Sites
   composer create-project drupal/recommended-project automated_testing_kit_recipe
1. Continue setup as normal (create a database, edit the settings.php file to point to the db, etc.)
1. Launch the site to complete the setup.
1. Use "admin" and "password" for the admin password (or the tests won't be able to log in). 
1. Once the site is set up, add this package to give composer more capabilities:
   composer require oomphinc/composer-installers-extender
1. Teach Composer about Recipe module types by adding this to your composer file:
  "installer-types": 
   ["drupal-recipe"],
  "installer-paths": {
    // existing entries omitted…
    "web/recipes/contrib/{$name}": [
     "type:drupal-recipe"
    ]
   }
1. Add this patch so Composer learns how to work with Recipes:
   "patches": {
     "drupal/core": {
       "Allow recipes to be applied":"https://git.drupalcode.org/project/distributions_recipes/-/raw/patch/recipe.patch"
     }
   }
1. Run the Recipe:
   cd web
   php core/scripts/drupal recipe recipes/contrib/atk_demo


## CONFIGURATION
The ATK Demo recipe provides all necessary configuration except for:
1. The Ethereal.mail account

See the project documentation for that at 
https://performantlabs.com/automated-testing-kit/automated-testing-kit

## MAINTAINERS

- André Angelantoni (aangel) - https://www.drupal.org/u/aangel

