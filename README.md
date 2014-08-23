# Dott -- simple dotfiles management

Dott is a simple shell script I wrote to manage [my dotfiles][]. It handles the
updating and symlinking into `$HOME` of all my dotfiles, kept in a Git
repository.

## Installation

To install dott, simply put the `dott` file somewhere in your `$PATH` and make it
executable. One way to do so would be:

    % curl https://raw.githubusercontent.com/avdgaag/dott/master/dott > /usr/local/bin/dott
    % chmod +x /usr/local/bin/dott

You can test if everything works alright by running `dott --version`. You should
see something along these lines:

    % dott --version
    0.1.0

## Usage

Here is the help contents displayed when you run `dott --help`:

    Usage: dott [subcommand] [options]
    
    Available subcommands:
    
      clone          Install dotfiles from a Git repository into ~/.dotfiles
      update         Fetch new commits from the remote repository and optionally
                     update subtree-merged remote repositories.
      link           Symlink all the files in the dotfiles directory into the
                     home directory.
      unlink         Remove symlinks to files in the dotfiles directory from
                     the home directory.
    
    Options for update:
    
      -s, --subtrees Also fetch new commits for merged subtrees and squash them
                     into the local repository. This reads subtree directories
                     and repositories from ~/.dotfiles/.gitsubtrees.
    
    Options for link:
    
      -f, --force    Overwrite files even if they already exist.
      -p, --pretend  Display results but don't actually change anything
    
    Options for unlink:
    
      -p, --pretend  Display results but don't actually change anything
    
    Generic options:
    
      -v, --version  Show version information
      -h, --help     Show this message

A normal workflow would be to first install your personal dotfiles from a Git
repository in your local home directory:

    % dott clone git@github.com:avdgaag/dotfiles.git

This will clone the repository into `~/.dotfiles`.

Then, symlink all the files from `~/.dotfiles/home` into `$HOME`:

    % dott link

To overwrite any existing files, use the `--force` flag:

    % dott link --force

To clean up again, remove all your symlinks using `unlink`:

    % dott unlink

To update your `~/.dotfiles` directory from its remote repository,
use `dott update`:

    % dott update

My personal dotfiles repo has a list of other repositories merged into it using
a Git subtree merge. Dott can update these repositories automatically by adding
the `--subtrees` flag to `dott update`:

    % dott update --subtrees

## Credits and links

**Author**: Arjan van der Gaag <arjan@arjanvandergaag.nl>
**Date**: August 2014
**Website**: http://avdgaag.github.io/dott
**Issues** https://github.com/avdgaag/dott/issues
**Source** https://github.com/avdgaag/dott
**Changelog** See CHANGELOG.md

## License

Dott is released under the MIT license (see LICENSE).

[my dotfiles]: https://github.com/avdgaag/dotfiles
