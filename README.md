# Source Removal Cloud Native Buildpack

This buildpack is meant to be used at the end of the buildpack order definition
and will delete files in the application directory.

## Buildpack Configuration

This buildpack will always pass detection will delete all files that are in
your application directory.There are two ways to control what files are deleted
by this buildpack.

### `$BP_INCLUDE_FILES`
If you want a specific subset of files to remain in your buildpacks application
directory flag them to be included using the environment variable
`$BP_INCLUDE_FILES` which is a list of globs.
```
$BP_INCLUDE_FILES=file/glob/*:file/some-file
```

### `$BP_EXCLUDE_FILES`
If you want a specific subset of files to be in your buildpacks application
directory flag them to be included using the environment variable
`$BP_EXCLUDE_FILES` which is a list of globs.
```
$BP_EXCLUDE_FILES=file/glob/*:file/some-file
```

### Overlapping logic
If both are set then the include logic will run followed by the exclude logic.

## Usage

To package this buildpack for consumption:

```
$ ./scripts/package.sh
```

This builds the buildpack's Go source using `GOOS=linux` by default. You can
supply another value as the first argument to `package.sh`.
