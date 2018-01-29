# phpenv-conf

This is a [`phpenv`](https://github.com/src-run/phpenv.git) plug-in providing PHP configuration (ini file)
management commands. On first invocation a `conf.d-available/` path is created parallel to the original
`conf.d/`, which provides the location this script places ini files when calling with `--[cfg|ext]-add`.
Actually enabling the ini file is done by calling `-e` or `--enable`, which symlinking the file from
`conf.d-available/` into `conf.d/`.

## Installation

__Automated Installation:__ If starting from scratch, you can use the [`phpenv`](https://github.com/src-run/phpenv.git)
installation script, which by default automatically installs this plug-in:

```bash
curl -s https://raw.githubusercontent.com/src-run/phpenv/master/bin/phpenv-installer-remote.bash | bash
```

__Manual Installation:__ Alternatively, you can clone the repository yourself into your `~/.phpenv/plugins` directory:

```bash
git clone https://github.com/src-run/phpenv-conf.git ~/.phpenv/plugins/php-conf
```

## Usage

```bash
phpenv conf [OPTION] [<cfgini|extini|extname|conf>]
```

### CLI Options

```bash
#add local general-purpose config ini file (ex.: defining timezone)
phpenv conf -c|--cfg-add <cfg-file>

#add a local extension config ini file (ex.: igbinary.ini, tidy.ini, etc)
phpenv conf -x|--ext-add <ext-file>

#create new extension config file from name (containing "extension=<extname>.so")
phpenv conf -X|--ext-new <ext-name>

#remove installed config completely (from active config and available config dirs)
phpenv conf -r|--rm <cfg-name>

#enable installed config (by symlinking from available dir)
phpenv conf -e|--enable <cfg-name>

#disable installed config (by removing enabled symlink)
phpenv conf -d|--disable <cfg-name>

#list both enabled and disabled configs 
phpenv conf -l|--list

#display installed config file contents
phpenv conf -s|--show <cfg-name>

#show version of php-congig (including current git hash)
phpenv conf -V|--version

#display help dialoge message (in fact, this message you'r reading here!)
phpenv conf -h|--help|help
```
