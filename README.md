# Mango

![banner](./public/img/banner-paddings.png)

Mango is a self-hosted manga server and reader. Its features include

- Multi-user support
- Supports both `.zip` and `.cbz` formats
- Automatically stores reading progress
- The web reader is responsive and works well on mobile, so there is no need for a mobile app
- All the static files are embedded in the binary, so the deployment process is easy and painless

## Installation

### Docker

1. Make sure you have docker installed and running
2. Clone the repository
3. `docker build -t mango:mango .`
4. `docker run -td --name mango -p 9000:9000 -v /path/to/your/mango/library:/root/mango/library mango:mango`
5. Now the docker container is up and running. You can get into it using `docker exec -it mango /bin/bash` and then start Mango using the command `mango`

### Build from source

1. Make sure you have Crystal, Node and Yarn installed
2. Clone the repository
3. `make && sudo make install`
4. Start mango by running the command `mango`

## Usage

### CLI

```
Mango e-manga server/reader. Version 0.1.0

    -v, --version                    Show version
    -h, --help                       Show help
    -c PATH, --config=PATH           Path to the config file. Default is `~/.config/mango/config.yml`
```

### Config

The default config file location is `~/.config/mango/config.yml`. The config options and default values are given below

```yaml
---
port: 9000
library_path: ~/mango/library
db_path: ~/mango/mango.db
scan_interval_minutes: 5
log_level: info
```

- `scan_interval_minutes` can be any non-negative integer. Setting it to `0` disables the periodic scan
- `log_level` can be `debug`, `info`, `warn`, `error`, `fatal` or `off`. Setting it to `off` disables the logging

### Required Library Structure

Please make sure that your library directory has the following structure:

```
.
├── Manga 1
│   └── Manga 1.cbz
└── Manga 2
    ├── Vol 0001.zip
    ├── Vol 0002.zip
    ├── Vol 0003.zip
    ├── Vol 0004.zip
    └── Vol 0005.zip
```

### Initial Login

On the first run, Mango would log the default username and a randomly generated password to STDOUT. You are advised to immediately change the password.

## Screenshots

Library:

![library screenshot](./.github/screenshots/library.png)

Title:

![title screenshot](./.github/screenshots/title.png)

Reader:

![reader screenshot](./.github/screenshots/reader.png)

Mobile UI:

![mobile screenshot](./.github/screenshots/mobile.png)
