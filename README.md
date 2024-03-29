# fs-native-extensions-nodejs-mobile

[NodeJS Mobile](https://github.com/nodejs-mobile/nodejs-mobile) prebuilds for [`fs-native-extensions`](https://github.com/holepunchto/fs-native-extensions).

## Working locally

### Requirements

- Node 18
- Android NDK 24.0.8215888
  - (optional) exported `ANDROID_NDK_PATH` environment variable

### General steps

Should be clear enough to follow the workflow steps but in summary:

1. Download the npm tarball package and unzip e.g. `npm pack fs-native-extensions@latest | xargs tar -zxvf`

2. Navigate to unzipped directory and run `npx prebuild-for-nodejs-mobile TARGET`, where `TARGET` is an accepted value from the [`prebuild-for-nodejs-mobile`](https://github.com/staltz/prebuild-for-nodejs-mobile) CLI
   - if you don't have the `ANDROID_NDK_PATH` environment variable exported, you may run the command like so: `ANDROID_NDK_HOME=/path/to/ndk npx prebuild-for-nodejs-mobile TARGET`

## Creating a release

1. Create a git tag that matches the version of the module you want to create prebuilds for e.g. `git tag 1.0.0`

2. Push the tag to the remote e.g. `git push origin 1.0.0`

3. The workflow uses the tag version to create the prebuilds and then publish a release with those prebuilds.

4. The relevant artifacts will show up in GitHub Releases. Each artifact is a tarball containing the `.node` files for the target-specific prebuild.
