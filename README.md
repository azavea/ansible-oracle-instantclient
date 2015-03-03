# ansible-oracle-instantclient

An Ansible role for installing the Oracle Database Instant Client.

## .deb packages

Oracle does not provide Ubuntu/Debian compatible packages. You will need to download "Basic", "SDK", and "Sql\*Plus" RPMs from http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html and use the alien tool to convert them.

`alien oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm`

## Role Variables

- `instantclient_libaio1_version` - libaio1 version (default `"0.3.109-4"`)
- `instantclient_oracle_package_dest` - where to download/copy Oracle packages; no trailing slash (default: `"/opt/oracle_packages"`)
- `instantclient_oracle_packages` - a list of dictionaries describing .deb packages that should be copied/downloaded (contains sensible defaults for files copied from local storage. See "Example Playbook" below.)
 - `filename` - the name of the file
 - `url` - the url the file should be downloaded from, if not copied from local storage
 - `sha256sum` - the sha256sum of the file if downloaded, to protect file integrity
- `instantclient_oracle_lib` - directory the packages create to be added to the system library list (default: `"/usr/lib/oracle/12.1/client64/lib/"`)
- `instantclient_oracle_home` - directory the packages create to be set as the value of the ORACLE_HOME environment variable (default: `"/usr/lib/oracle/12.1/client64"`)
- `instantclient_oracle_package_src` - directory on the local machine where packages are stored, if not downloading; no trailing slash

## Example Playbook

See the [examples](./examples/) directory. Place `oracle-instantclient12.1-basic_12.1.0.2.0-2_amd64.deb`, `oracle-instantclient12.1-devel_12.1.0.2.0-2_amd64.deb`, and `oracle-instantclient12.1-sqlplus_12.1.0.2.0-2_amd64.deb` in `~/oracle`.
