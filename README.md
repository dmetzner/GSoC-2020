## Background

The **[Share community platform](https://share.catrob.at/app/)** is a web application responsible for hosting dynamic user data of [Catrobats](https://www.catrobat.org/)' [app](https://wiki.catrobat.org/bin/view/AboutCatrobat/CatrobatApps/) users, including more than 180 thousand projects. Besides, the platform provides various recommendations, social features, tutorials, and much more. The platform, also often referred to as [Catroweb](https://github.com/Catrobat/Catroweb), is developed using the [Php](https://www.php.net/manual/de/intro-whatis.php) web-framework [Symfony](https://symfony.com/) in a test-driven development. However, over the years, many components of the project became outdated and broken, leaving the project hard to maintain with low usability. The Catroweb team does its best to refactor and update every feature to increase software quality. Nevertheless, the resources are limited in the Catrobat project.
 
[Google Summer of Code (GSoC)](https://summerofcode.withgoogle.com/) is a global program that matches students up with open-source, free software, and technology-related organizations to write code and get paid to do it. This **GSoC project** is fully dedicated to further **improve the performance, code quality, and design** to satisfy the requirements of customers and developers in the **Catrobat/Catroweb** project.

This report describes my GSoC 2020 contributions to the Catroweb project. A significant part of my work started with the **research and planning** aspects **of the refactoring**. Every **pull request of other developers** during this project was **extensively reviewed** and discussed.  Apart from that, **various measurements and new features** have been **implemented** by myself.

## Phase 1 - Identification of issues

#### Code quality: 
- The CI/CD system currently in development (not part of this project) using GitHub actions introduced various **static analysis tools** in addition to the dynamic tests. Using their results enables quick **localization of code smells** and bad practices hidden deeply in the project.

- With manual **code reviews** of new contributions and also of the existing codebase, many issues can be detected.

#### Performance:
-  To analyze the platform's performance, a development tool provided by Google called [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) is used. **PageSpeed Insights** offers extensive details about the impact of possible issues. 

#### Design:
- No research was needed. It was already clear that the whole page should get a new skin.

## Phase 2 - Planning

1.  All the identified issues **tickets** have been **created** to keep track of their state in [Jira](https://www.atlassian.com/de/software/jira). Jira is a tool to manage and monitor the development process heavily used in the Catrobat project and its agile development. Various tickets required the input of the UX-team. The UX-team is responsible for creating mock-ups and defining the workflow of a new feature. However, a part of this project was to constantly provide the UX team with extensive feedback to ensure the features are fully specified. The conversations are not publicly available. (PM, or [Catrobats confluence pages](https://confluence.catrob.at/))

2. Presenting all issues in a **planning game** to the whole team collectively estimate the required work to implement the tickets. Besides, this provides all developers with a short overview of the topic. This way, everyone can quickly start to work on any of the defined issues. [Here](https://docs.google.com/spreadsheets/d/1a6zUVBO7E9PENKcAw1-RSjDckfzoV2y1BKmnt1ZFEZw/edit?usp=sharing) is the Google spreadsheet created for this process.

## Phase 3 - Implementing all tickets

#### CodeReviews
Other members of the Catroweb team coded many of the specified issues. However, I did the code reviews. Some reviews were quick, while others, especially those for junior developers, were more extensive.

-   For example, the first part of the new Notifications Design can be seen here: [Example code review](https://github.com/Catrobat/Catroweb/pull/798). However, most conversations at Catrobat happened in Slack/Discord.

Here is the whole list of (~200) pull requests I have reviewed: [Reviewed pull request newer than 2020-05-01 (Catrobat/Catroweb)](https://github.com/Catrobat/Catroweb/pulls?page=8&q=is%3Apr+reviewed-by%3Admetzner+created%3A%3E%3D2020-05-01), [Reviewed pull request newer than 2020-05-01 (Catrobat/Catroweb-API)](https://github.com/Catrobat/Catroweb-API/pulls?q=is%3Apr+involves%3Admetzner+created%3A%3E%3D2020-05-01).

#### Coding

My created pull requests can be seen here: [Only pull request newer than 2020-05-01](https://github.com/Catrobat/Catroweb/pulls?q=is%3Apr+author%3Admetzner+created%3A%3E%3D2020-05-01+)). However, some of the pull requests were not created for GSoC, but the CI/CD system I am working on right now. Therefore, here is an explicit list of most commits that were done as a GSoC contribution.

##### New Features
- [Serve images as webp](https://github.com/Catrobat/Catroweb/pull/829)
- [Introduce Material.io to the project + new AppTopBars](https://github.com/Catrobat/Catroweb/commit/9144368dbd7e30f7c28e3b947205a13323dd44d5)
- [Download multiple media library files](https://github.com/Catrobat/Catroweb/commit/69ff464c4d75a4f4a8137130e23f7c37efd80977) ([disabled in web-view until apps provide support ](https://github.com/Catrobat/Catroweb/commit/a366e23ae5d6035e81f03bd8a03ee927783ca97d))
- [Exit Community Button](https://github.com/Catrobat/Catroweb/commit/aa87311e9fa6e3e75e8890570e5ab8bce292569d)
- [API health route](https://github.com/Catrobat/Catroweb/commit/7e67ea74fbf82c93c2b9a243a294134f8edbdbfd)

##### Redesign of:
- [Typography](https://github.com/Catrobat/Catroweb/commit/e1aa2610d4adb8b27510f42225182efa5ab22f5a)
- [Code Statistics](https://github.com/Catrobat/Catroweb/commit/01e917b6a7fa5a4af2b9249d1e308f0bf92ae6e7)
- [Code View](https://github.com/Catrobat/Catroweb/commit/45df603a107efefbb13362a3c6c1f21d7584264f)
- [Follower - refactorings and fixes](https://github.com/Catrobat/Catroweb/commit/1c17d51728974db1bb99d5aac33b58a4b61a3371)
- [ProjectList - final adjustments](https://github.com/Catrobat/Catroweb/pull/793/commits/668bb1fdf34dfa244cc52cde36663ab37f9ebd10)
- [Embroidery flavor](https://github.com/Catrobat/Catroweb/commit/8b9d83cf47af78184b5d88ce0356f2a4a63da53c) + [part 2](https://github.com/Catrobat/Catroweb/commit/d864ceced09e0dbe73f95c8bb1a4d2d56a41cb1c)

##### Refactor of:
- [API](https://github.com/Catrobat/Catroweb/commit/b1445d245b5f22b20fd1d98586710ff8c18bc65a)
- [Codestats/view and remixes on their own pages](https://github.com/Catrobat/Catroweb/commit/b67187f15fb7d420303ac78b7c6917abe3a49449)
- [Project structure, deprecating old API and minor issues](https://github.com/Catrobat/Catroweb/commit/81b9a18b53fea4135c12385504692b442a198ed6)
- [SASS code style](https://github.com/Catrobat/Catroweb/commit/f39d9986462ca446572259c4f7cf82867cf74c6d)
- [Minor changes, admin interface, report controller, profiler](https://github.com/Catrobat/Catroweb/commit/3a6b8bb61a255dbdc8c5732999bc2c7fad513bc1)

##### Removed dead/broken/duplictaed code in: 
- [Limited Users](https://github.com/Catrobat/Catroweb/commit/4211082033c1ca7c4983cc2522da43a558c42a0c)
- [Backup](https://github.com/Catrobat/Catroweb/commit/75484badd54d296cae5cb4501b41c551bfee2c34)
- [Commands](https://github.com/Catrobat/Catroweb/commit/735e404d3f44ee7a3445a962b32a0bc0ec1beaf8)
- [Entities](https://github.com/Catrobat/Catroweb/commit/3cc6254b6e93b4362be2d761da2cd1c05652bcc6)

##### Fixed Bugs/Issues:
- [Debug projects only hidden in production](https://github.com/Catrobat/Catroweb/commit/7653bd9fee7cc16ed9d7bed85deebbd2fe1d7a7d)
- [Fixed alpine-chrome version](https://github.com/Catrobat/Catroweb/commit/b0d1ab99c9d6b3f809a0e6c4b625f7dce590047d)
- [Project data was not updated correctly](https://github.com/Catrobat/Catroweb/commit/a321910c50780191efd1d1a1301f956e5ac999f0)
- [Sanitizer for preview images](https://github.com/Catrobat/Catroweb/pull/866/commits/3c8d31459839acb6c6591a58af6d750078f53358)
- [Deprecated Google Sign in](https://github.com/Catrobat/Catroweb/commit/0b75cad997156d52160aae70dcd41c64edb3f336)
- [iOSwebView](https://github.com/Catrobat/Catroweb/commit/1f56ea6749d0c7100b82168b8030456a4cdebfc8)
- [Logging](https://github.com/Catrobat/Catroweb/commit/d01c1d5b1c66ad61abe5c3114047ca1119a351cb)
- [Translations](https://github.com/Catrobat/Catroweb/commit/11442a3da87fdd13203a6e7852e303534d4edce3)
- [No search on code view pages](https://github.com/Catrobat/Catroweb/commit/eb79860a936f08545dd21828e1cc2da88719ca10)
- [Featured projects visibility](https://github.com/Catrobat/Catroweb/commit/f11dc915d6815fe70608623ccaa8fc6650953da7)
- [Minor changes](https://github.com/Catrobat/Catroweb/commit/601e94622333d043d15c5a2d6c031723a68be8aa)
- [Division by zero in recommendation system](https://github.com/Catrobat/Catroweb/commit/9cf1cdfc2b36b189eeba1d72e39a168bd04cd477)
- [Project structure](https://github.com/Catrobat/Catroweb/commit/d4763ce06231248b01481f66f9edcfaac1a55df3)
- [Debug projects in search](https://github.com/Catrobat/Catroweb/commit/e4f8b90e66648cca319bae205a66faefb23e34e1)
- [Unit translations](https://github.com/Catrobat/Catroweb/commit/885981f703d8255781355b43fd9d41280ea2f48b)
- [Docker missing shared volume](https://github.com/Catrobat/Catroweb/commit/92b4d6a1a841f71122d54d327728b9f5dd4d4482)
- [Loading of youtube js](https://github.com/Catrobat/Catroweb/commit/2b5736bb0c0861621f672f9164bbc7a1680a0d24)
- [Hotfix apple app site association](https://github.com/Catrobat/Catroweb/pull/865/commits/923fae664166b682ebe3724f27bcffe0991559c5)
- [Updated/removed many dependencies](https://github.com/Catrobat/Catroweb/pulls?q=is%3Apr+involves%3Admetzner+involves%3Adependabot)  (most work was done by  [Dependabot](https://dependabot.com/), only deprecations had to be fixed manually)

## Future work

The Catroweb project slowly finds itself in a stable state again. A software product will never be perfect. The goal is to find a balance between software quality and the required resources to achieve it. The following bullet points represent actions with a high return of investment. However, they were not possible to be implemented at the moment.

##### Currently NOT possible

-   **Php 8**: The next release of Php brings various new features such as [the JIT compiler](https://stitcher.io/blog/new-in-php-8#jit-rfc), [union types](https://stitcher.io/blog/new-in-php-8#union-types-rfc), and [attributes](https://stitcher.io/blog/new-in-php-8#attributes-rfc). The deprecations are already resolved. An upgrade should be easy.

-   **Symfony 5**: [The newest release of Symfony](https://symfony.com/5) comes with several improvements. One of them is a better performance. However, several dependencies block the upgrade at the moment ([SonataUserBundle](https://github.com/sonata-project/SonataUserBundle/issues/1112), [FOSElasticaBundle](https://github.com/FriendsOfSymfony/FOSElasticaBundle/issues/1624)). Other deprecations are already almost all resolved. Once there is no problem with the dependencies, the update should be easy.

##### Not possible in the given time frame:

- The **recommendation system** must be refactored. A single run takes 90 days + it always starts from scratch.

- The **remix graph system** must be refactored. Remixes for projects with many remixes load very slow + DB queries are executed with a size of multiple KB.
