# KeePassHTTP

[![pypi_version.svg][pypi_version.svg]][pypi_project.url]
[![pypi_status.svg][pypi_status.svg]][pypi_project.url]
[![pypi_format.svg][pypi_format.svg]][pypi_project.url]
[![python_versions.svg][python_versions.svg]][pypi_project.url]  
[![license.svg][license.svg]][license.url]
[![travis_build.svg][travis_build.svg]][travis.url]
[![codecov.svg][codecov.svg]][codecov.url]
[![requirements_status.svg][requirements_status.svg]][requires.url]
[![code_size.svg][code_size.svg]][pypi_project.url]
[![pypi_downloads.svg][pypi_downloads.svg]][pypi_project.url]


Python client for [KeePassHTTP][keepasshttp.url] to interact with [KeePass][keepass.url]'s credentials.


## Install

    $ pip install keepasshttp
    

## Usage

    import keepasshttp
    
    # get single credential
    credential = keepasshttp.get("my_credential_name_or_url")
    print(credential.login)
    print(credential.password)
    
    # find all credentials's name
    credentials = keepasshttp.list()
    
    # fetch all partiall matching credentials
    credentials = keepasshttp.search("my_credential_name_or_url")
    
    # create a new keepasshttp entry
    keepasshttp.create("login", "password", "url")
    
    # update a keepasshttp entry
    credential.password = "new password"
    # or
    keepasshttp.update("login", "password", "url", "uuid")


## Configuration

By default, this module will write AES association key to `~/.python_keepass_http`
and use `http://localhost:19455/` to connect to the [KeePassHTTP][keepasshttp.url] server.

To change theses parameters, instanciate `keepasshttp.KeePassHTTP` class with different values.

    from keepasshttp import KeePassHTTP
    kph = KeePassHTTP(
        storage='./keepasshttp_key', 
        url="https://example.com:1337/)
    kph.get("...")
    ...
    
    
## Testing

You can simply run the tests using:

    python -m unittest discover
    
`KeePassHTTP` calls are mocked, to run the tests against a real server, you need to:
 
   - open `tests/test_database.kdbx` in `KeePass` password is `test`
   - set `TEST_WITH_KEEPASS` environment variable
   - run test normally


## Coverage

To run tests with coverage:

    pip install pytest-cov
    pytest --cov
    

[comment]: # (Urls references)
[pypi_project.url]: https://pypi.org/project/keepasshttp/
[license.url]: ./LICENSE.txt
[travis.url]: https://travis-ci.org/cyrbil/python_keepass_http
[codecov.url]: https://codecov.io/github/cyrbil/python_keepass_http
[requires.url]: https://requires.io/github/cyrbil/python_keepass_http/requirements/?branch=master
[keepasshttp.url]: https://github.com/pfn/keepasshttp
[keepass.url]: https://keepass.info/

[comment]: # (Images references)
[pypi_version.svg]: https://img.shields.io/pypi/v/keepasshttp.svg "PYPI KeePassHTTP"
[pypi_status.svg]: https://img.shields.io/pypi/status/keepasshttp.svg "PYPI KeePassHTTP"
[pypi_format.svg]: https://img.shields.io/pypi/format/keepasshttp.svg "PYPI KeePassHTTP"
[python_versions.svg]: https://img.shields.io/pypi/pyversions/keepasshttp.svg "PYPI KeePassHTTP"
[license.svg]: https://img.shields.io/github/license/cyrbil/python_keepass_http.svg "MIT"
[travis_build.svg]: https://img.shields.io/travis/cyrbil/python_keepass_http/master.svg "travis.org"
[codecov.svg]: https://codecov.io/github/cyrbil/python_keepass_http/coverage.svg?branch=master "codecov.io"
[requirements_status.svg]: https://img.shields.io/requires/github/cyrbil/python_keepass_http.svg "requires.io"
[code_size.svg]: https://img.shields.io/github/languages/code-size/cyrbil/python_keepass_http.svg "All files"
[pypi_downloads.svg]: https://img.shields.io/pypi/dm/keepasshttp.svg "PYPI KeePassHTTP"
