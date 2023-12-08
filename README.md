## Experimental warning
This extension is currently in an experimental state. Feel free to try it out, but be aware some things
may not work as expected.

# DuckDB Azure Extension
This extension adds a filesystem abstraction for Azure blob storage to DuckDB. To use it, install latest (>0.9.1) DuckDB
and run: 
```sql
SET azure_storage_connection_string = '<your_connection_string>';
```
then you can query files from azure:
```sql
SELECT count(*) FROM 'azure://<my_container>/<my_file>.<parquet_or_csv>';

```

## Supported architectures
The extension is tested & distributed for Linux (x64, arm64), MacOS (x64, arm64) and Windows (x64)

## Documentation

See the [Azure page in the DuckDB documentation](https://duckdb.org/docs/extensions/azure).

Check out the tests in `test/sql` for more examples.

## Building
This extension depends on the Azure c++ sdk. To build it, either install that manually, or use vcpkg
to do dependency management. To install vcpkg check out the docs [here](https://vcpkg.io/en/getting-started.html).
Then to build this extension run:

```shell
VCPKG_TOOLCHAIN_PATH=<path_to_your_vcpkg_toolchain> make
```

## Example - Building on Ubuntu 22.04

```shell
# Checkout source and submodule
git clone --recurse-submodules https://github.com/duckdb/duckdb_azure.git && cd duckdb_azure

# Install vcpkg in root of azure_duckdb source path
git clone https://github.com/Microsoft/vcpkg.git

# Run the bootstrap script to build vcpkg
vcpkg/bootstrap-vcpkg.sh

# Install dependencies
vcpkg/vcpkg install

# Make
VCPKG_TOOLCHAIN_PATH=$PWD/vcpkg/scripts/buildsystems/vcpkg.cmake make
```
