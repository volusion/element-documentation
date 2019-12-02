# Block Versions

Blocks are a foundation concept of the Element platform. As blocks are Javascript applications that can be used by many sites, we
need effective ways to handle the release cycles of the block's code. We want to publish changes in a fearless way, protecting the current
users of our blocks, but also, adding new features or fixing bugs when required.

## Staging vs Production

A block is in staging mode when you have published changes, but the changes are not released yet. Every time you publish new code, the system will create
a staging version that is only visible to you and the members of your org. Thanks to this protection, even if your block is being used by thousands
of users, they won't see the changes that you are making. The staging mode is useful while developing or making changes to blocks.

When you are ready you can make your code generally available by releasing your changes, promoting your changes from staging to production mode. When
you release a change, you have two options, a minor or a major release.

## Minor vs Major Release

A block can have multiple major versions. And inside each major version, a block may have many minor releases.

This is the difference between a minor and a major release:

**Minor releases** are propagated automatically to all the users of your block. This is a really convenient way of shipping bug fixes and new features that don't affect the block look and feel or the block configuration. The block users need to perform no action in order to get your updates.

**Major releases** are not propagated automatically and users need to manually opt-in for the new block versions. Major releases are important to ship new features on a block that are not compatible or can potentially change the look and feel of current storefronts.

Major releases are tagged internally with ascending numbers, starting from one. Each new version will increment the number by one. For minor versions, there is no explicit numeric tagging, but it is a good practice to
tag your minor releases using git or similar. For more details, see [how to keep track of your block versions](TODO - link)
