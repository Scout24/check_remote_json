Simple Nagios/Icinga check for remote query with JSON output
============================================================

# This project is DEPRECATED and not any longer supported

Did you every try to use check_http to check a web service that talks JSON? I did and it is no fun. This check queries a remote URL and expects JSON output with a status and message field, for example like this:
```json
{
    "message": "",
    "status": 0,
}
```
Or, to indicate a error situation:
```json
{
    "message": "Foo is really getting the bar up today, please fix the baz.",
    "status": 2,
}
```
In fact, any status that is *not* 0 will lead to a critical result (exit code 2) of the check.

Usage
-----

Simply call `check_remote_json` with the URL to check. Optionally use `-v` to always see the full response body. Example using the vSphere time sync check available in [Lab Manager Light](https://github.com/ImmobilienScout24/lab-manager-light/commit/3c3799f19decee30941e2c7652843b16da5ded84):
```bash
$ check_remote_json http://some.host.name/lml/hostdatetime.pl
```

