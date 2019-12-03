# How to Keep Track of Your Block Versions

In this how-to guide we will explore how to keep track of block versions to maintain your block's code organized. We will assume that you are already
developing a block locally and want to publish your block for the first time.

An explanation about [Block Versions](../../explanation/block-versions/README.md) is a recommended read.

## 1. Initialize a Git Repository with Your Block Code 

If you haven't already, we really recommend you to keep your code organized using `git`. It's as easy as running:

```bash
git init
```

Also, remember that you can create the repo while creating your block by running:

```bash
element new --git MyBlock
```

## 2. Publish Your Block for the First Time

It's time to test your work online, both in the Site Designer and in a live domain. To do that, let's publish the block:

```bash
npm run build
element publish -n "My Block Name"
```

## 3. Use and Test Your Block Online

Go to the Site Designer and install your block in one of your pages. Play with it, test the configuration and see how it looks in the preview domain.

## 4. Keep Developing

Every time you want to test your changes online, just run:

```bash
npm run build
element update
```

This will push the code updates online. The block is still in staging mode.

## 5. Create Your First Major Release

You are ready to make your first major release.

```bash
npm run build
element update
element release -n "Release note"
```

The release note is optional.

Here it is a good moment to commit the change to git.

```
git commit -m "First major release"
```

## 6. Create a Minor Release

Once you published your first major release, you can publish as many minor releases as you want. The minor release are linked to your major release.

```bash
element update
```

Remember that every time you issue an update with `element update` a staging version is created, so your block users won't be affected by your changes.

## 7. Release the Minor Version

Once your change is ready to reach your users, just release it. It is also a good moment to tag the release with a commit.

```bash
npm run build
element update
element release -n "A minor release"
git commit -m "A minor release"
```

## 8. Rolling Back a Minor Release (When Needed)

If you published a minor change and for some reason want to roll it back, you can also do it.

```
element rollback
```

If you had multiple minor releases linked to the major release, every `rollback` command will jump back one release until reaching the major. The major version
cannot be rolled back.

Every time you run it, remember to point your repo to the right commit to have the same code locally and in the Element servers.

```
git checkout "commit_id_of_previous_minor_releas"
```

## 9. Creating a New Major Version

Sometimes you will need to publish a new version of your block, with new feature, breaking changes or something that diverges a bit from the original one.

```
element publish -m
```

The `-m` versions stands for `major` and will create a branch for you with the name of the next version. If you are in version 1 for example and run the command,
a branch called `v2` will be created. Additionally the block will be published to the servers with the new version but not yet released. You can repeat steps
3 to 8 as needed for the new version.

If you need to release changes for different block versions, just change to the appropriate branches.


