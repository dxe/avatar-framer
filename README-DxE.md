The README.md in this directory came with the repo we forked this from. This
README file contains instructions specific to DxE's usage.

Use the devcontainer configuration in this project to avoid installing Jekyll
and Node on your personal computer.

To deploy this project, update the cachebusting args as instructed in the main
README, run `pnpm run build` and copy the contents of the `_site` directory of
this repo to the `frame-generator` directory of our
[static-s3 repo](https://github.com/dxe/static-s3/), and follow the S3 repo's
instructions for deploying to AWS S3.

```bash
# Remember to update cachebust args!
jekyll build
pnpm run build
cd ../static-s3/
git pull
rm -rf ./frame-generator/ --preserve root
cp -r ../avatar-framer/_site/ ./frame-generator/
cd ./frame-generator/
git add .
git status
git commit -m "Update avatar-framer"
git push
cd ../../avatar-framer
# Remember to update cache busting version in dxe.io/frame shortlink too.
```
