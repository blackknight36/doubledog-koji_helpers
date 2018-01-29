# koji\_helpers

#### Table of Contents

1. [Description](#description)
1. [Setup - The basics of getting started with koji\_helpers](#setup)
    * [What koji\_helpers affects](#what-koji\_helpers-affects)
    * [Setup requirements](#setup-requirements)
    * [Beginning with koji\_helpers](#beginning-with-koji\_helpers)
1. [Usage - Configuration options and additional functionality](#usage)
1. [Reference - An under-the-hood peek at what the module is doing and how](#reference)
    * [Classes](#classes)
    * [Defined types](#defined-types)
1. [Limitations - OS compatibility, etc.](#limitations)
1. [Development - Guide for contributing to the module](#development)

## Description

This module lets you manage the koji-helpers package and its configuration.  That package, however, has not yet been released to the general public so this is not likely to be of any value to you.  Sorry kids.

## Setup

### What koji\_helpers Affects

### Setup Requirements

### Beginning with koji\_helpers

## Usage

## Reference

**Classes:**

* [koji\_helpers](#kojihelpers-class)

**Defined types:**


### Classes

#### koji\_helpers class

This class manages the package installation, the work directory along with the gojira and smashd services.  It also anchors the various configuration fragments that govern those services.

##### `notifications_to` (required)
An array of email address that are to be notified when smashd affects package repositories.

##### `repo_dir` (required)
Name of the directory that is to be synchronized with the repository tree composited from each of the mashed repositories.  This typically would be the longest path that all package repositories have in common.

##### `repo_owner` (required)
User that is to own the `repo_dir` and the content therein.

##### `exclude_tags`
An array of tags which smashd should ignore.  The default is `['trashcan']`.

##### `enable`
Services are to be started at boot.  Either `true` (default) or `false`.

##### `ensure`
Services are to be `running` (default) or `stopped`.  Alternatively, a Boolean value may also be used with `true` equivalent to `running` and `false` equivalent to `stopped`.

##### `notifications_from`
The email address to be used as the sender when smashd sends notifications.  Defaults to `repo_owner` @ the (facter) `$domain`.


### Defined types


## Limitations

Tested on modern CentOS releases, but likely to work on any Red Hat variant.  Adaptations for other operating systems should be trivial as this module follows the data-in-module paradigm.  See `data/common.yaml` for the most likely obstructions.  If "one size can't fit all", the value should be moved from `data/common.yaml` to `data/os/%{facts.os.name}.yaml` instead.  See `hiera.yaml` for how this is handled.

This should be compatible with Puppet 4.x.

## Development

Contributions are welcome via pull requests.  All code should generally be compliant with puppet-lint.