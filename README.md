Do not push any code to that repository.

# How to publish
1. On https://github.com/nextcloud, tag appropriate commit on the source repository
2. Push the new tag to this repository
3. Create release on this repository

# Automatic package and publish
1. Make sure you have the [necessary workflow](https://github.com/nextcloud/.github/blob/master/workflow-templates/appstore-build-publish.yml) on your https://github.com/nextcloud source repository
2. Make sure your tagged commit also have the workflow
3. Make sure this repository have the proper `APP_PRIVATE_KEY` secret set
4. Make the `nextcloud_release_service` user is a co-maintainer of your app on https://apps.nextcloud.com/
5. Make sure you have admin rights to this repository

# Checklist for the pull request

## Release pull request

- [ ] Pull latest stable branch `git checkout stableX`
- [ ] Branch off a release branch `git checkout -b release/X.X.X`
- [ ] Bump versions
  - [ ] appinfo/info.xml
  - [ ] package.json
  - [ ] package-lock.json
- [ ] Update changelog
- [ ] Commit the version bump and push to origin 
- [ ] Merge release pull request

## Release the app

- [ ] Once merged, checkout the stable branch again `git checkout stableX` and `git pull`
- [ ] Tag a new release `git tag vx.x.x`
- [ ] Push tag
  - [ ] to the main repo: `git push origin stableX --tags`
  - [ ] to the release repo: `git push release stableX --tags`
- [ ] Build release on https://github.com/nextcloud-releases/user_oidc/tags
  - [ ] Draft a new release with the tag, add the changelog and publish
  - [ ] Wait a few minutes for the automation to build the app and to be published to the App Store

