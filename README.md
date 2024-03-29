# openwsman Builder for Debian 11
This repository contains the code which builds openwsman for Debian 11.

This also builds packages for sblim-sfcc since libcimcclient0-dev is a build-time dependency for openwsman.

To execute, simply run `do_build.sh`

If you have not already, `docker pull debian:11.5-slim`

When finished, the files will be in artifacts, and the directory will be usable as a Debian repository.

NOTE: This builds python3 bindings and *only* python3 bindings; python 3.9 to be precise. This is in contrast to the original package which only builds python2 bindings.

Pull requests which build for other Python versions would be welcome. My cmake experience is very minimal, thus the single Python version.

To use the repo generated by this script, put this in a Debian source file

```deb [trusted=yes] https://<CI Server URL>/<Path to Job>/artifacts/debs/ ./```

For example, in Jenkins, you can do:

```deb [trusted=yes] https://<CI Server URL>/job/<Path to Job>/lastSuccessfulBuild/artifact/artifacts/debs/ ./```

This was all constructed by someone who is very much a Debian packaging novice, so it is very possible there are some best practices not implemented. Again: PRs welcome!
