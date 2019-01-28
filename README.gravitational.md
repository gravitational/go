To create Gravitational build of Go.

**Backport Fix**

First clone `git clone git@github.com:gravitational/go.git` and checkout our backport branch: `git checkout release-branch.go1.9-g`. Then cherry-pick the fix back to our branch.

**Build Release**

Update `VERSION`. You'll want to update the version after `-g`. For example if the current version is `go1.9.7-g.1` you want to update it to `go1.9.7-g.2`.

Then run `GOROOT_BOOTSTRAP=/usr/local/go ./make.bash` from the `src` directory.

Validate the release by checking that the binary is the latest version by running `./go version` from the `bin` directory.

**Create Archive**

Create archive by first removing the `.git` directory then running the following command from the parent directory of `go`:  `tar -czvf go1.9.7-g.1.linux-amd64.tar.gz go)`.

Lastly create a checksum: `sha256sum go1.9.7-g.1.linux-amd64.tar.gz > go1.9.7-g.1.linux-amd64.tar.gz.sha256`

**Upload to S3**

Upload to our S3 bucket.
