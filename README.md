# Installation

Install r10k via Ruby Gems.

```
gem install r10k
```

Configure r10k by creating the following directory structure and file /etc/puppetlabs/r10k/r10k.yaml and ensuring it has the following contents:

```
# The location to use for storing cached Git repos
:cachedir: '/var/cache/r10k'

# A list of git repositories to create
:sources:
  # This will clone the git repository and instantiate an environment per
  # branch in /etc/puppetlabs/code/environments
  :my-org:
    remote: 'git@github.com:$_Insert GitHub Organization Here_$/$_Insert GitHub Repository That Will Be Used For Your Puppet Code Here_$'
    basedir: '/etc/puppetlabs/code/environments'
```

Ensure that the user r10k runs as (typically root) can access the git repository.

Recursively update all environments:

```
r10k -v deploy environment
```

