# Rinvex Contacts

**Rinvex Contacts** is a polymorphic Laravel package, for contact management system. You can add contacts to any eloquent model with ease.

[![Packagist](https://img.shields.io/packagist/v/rinvex/contacts.svg?label=Packagist&style=flat-square)](https://packagist.org/packages/rinvex/contacts)
[![VersionEye Dependencies](https://img.shields.io/versioneye/d/php/rinvex:contacts.svg?label=Dependencies&style=flat-square)](https://www.versioneye.com/php/rinvex:contacts/)
[![Scrutinizer Code Quality](https://img.shields.io/scrutinizer/g/rinvex/contacts.svg?label=Scrutinizer&style=flat-square)](https://scrutinizer-ci.com/g/rinvex/contacts/)
[![Code Climate](https://img.shields.io/codeclimate/github/rinvex/contacts.svg?label=CodeClimate&style=flat-square)](https://codeclimate.com/github/rinvex/contacts)
[![Travis](https://img.shields.io/travis/rinvex/contacts.svg?label=TravisCI&style=flat-square)](https://travis-ci.org/rinvex/contacts)
[![SensioLabs Insight](https://img.shields.io/sensiolabs/i/8f0346d3-9e8c-4044-9b14-49a858b882d6.svg?label=SensioLabs&style=flat-square)](https://insight.sensiolabs.com/projects/8f0346d3-9e8c-4044-9b14-49a858b882d6)
[![StyleCI](https://styleci.io/repos/97991812/shield)](https://styleci.io/repos/97991812)
[![License](https://img.shields.io/packagist/l/rinvex/contacts.svg?label=License&style=flat-square)](https://github.com/rinvex/contacts/blob/develop/LICENSE)


## Installation

1. Install the package via composer:
    ```shell
    composer require rinvex/contacts
    ```

2. Execute migrations via the following command:
    ```
    php artisan migrate --path="vendor/rinvex/contacts/database/migrations"
    ```

3. **Optionally** you can publish migrations and config files by running the following commands:
    ```shell
    // Publish migrations
    php artisan vendor:publish --tag="rinvex-contacts-migrations"

    // Publish config
    php artisan vendor:publish --tag="rinvex-contacts-config"
    ```

4. Done!


## Usage

### Create Your Model

Simply create a new eloquent model, and use `\Rinvex\Contacts\HasContacts` trait:
```php
namespace App\Models;

use Rinvex\Contacts\HasContacts;
use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    use HasContacts;
}
```

### Manage Your Contacts

```php
$user = new \App\Models\User();

// Create a new contact
$user->contacts()->create([
    'name_prefix' => 'Mr.',
    'first_name' => 'Abdelrahman',
    'middle_name' => 'Hossam M. M.',
    'last_name' => 'Omran',
    'name_suffix' => null,
    'job_title' => 'Software Architect',
    'email' => 'me@omranic.com',
    'phone' => '+201228160181',
    'source' => 'website',
    'method' => 'call',
    'country_code' => 'eg',
    'language_code' => 'en',
    'birthday' => '1987-06-18',
    'gender' => 'm',
    'is_active' => 1,
]);

// Create multiple new contacts
$user->contacts()->createMany([
    [...],
    [...],
    [...],
]);

// Find an existing contact
$contact = \Rinvex\Contacts\Contact::find(1);

// Update an existing contact
$contact->update([
    'email' => 'iOmranic@gmail.com',
]);

// Delete contact
$contact->delete();

// Alternative way of contact deletion
$user->contacts()->where('id', 123)->first()->delete();

// Get relative contacts collection
$user->relatives;

// Get relative contacts query builder
$user->relatives();

// Get back relative contacts collection
$user->backRelatives;

// Get back relative contacts query builder
$user->backRelatives();

// Get attached contacts collection
$user->contacts;

// Get attached contacts query builder
$user->contacts();
```


## Changelog

Refer to the [Changelog](CHANGELOG.md) for a full history of the project.


## Support

The following support channels are available at your fingertips:

- [Chat on Slack](http://chat.rinvex.com)
- [Help on Email](mailto:help@rinvex.com)
- [Follow on Twitter](https://twitter.com/rinvex)


## Contributing & Protocols

Thank you for considering contributing to this project! The contribution guide can be found in [CONTRIBUTING.md](CONTRIBUTING.md).

Bug reports, feature requests, and pull requests are very welcome.

- [Versioning](CONTRIBUTING.md#versioning)
- [Pull Requests](CONTRIBUTING.md#pull-requests)
- [Coding Standards](CONTRIBUTING.md#coding-standards)
- [Feature Requests](CONTRIBUTING.md#feature-requests)
- [Git Flow](CONTRIBUTING.md#git-flow)


## Security Vulnerabilities

If you discover a security vulnerability within this project, please send an e-mail to [help@rinvex.com](help@rinvex.com). All security vulnerabilities will be promptly contacted.


## About Rinvex

Rinvex is a software solutions startup, specialized in integrated enterprise solutions for SMEs established in Alexandria, Egypt since June 2016. We believe that our drive The Value, The Reach, and The Impact is what differentiates us and unleash the endless possibilities of our philosophy through the power of software. We like to call it Innovation At The Speed Of Life. That’s how we do our share of advancing humanity.


## License

This software is released under [The MIT License (MIT)](LICENSE).

(c) 2016-2017 Rinvex LLC, Some rights reserved.
