---
layout: post
title: Drupal Gitlab Merge Request Workflow explained.
description: >-
  With the introduction of Merge Request workflow in Drupal Gitlab, It is now
  easier than ever to contribute to Drupal via code.
date: '2020-11-21T10:28:58.857Z'
categories: []
keywords: []
migrated_source: 'Medium'
migrated_url: 'https://jaykandari.medium.com/drupal-gitlab-merge-request-workflow-explained-e58e22efadd7'
---

> With the introduction of Merge Request workflow in Drupal Gitlab, It is now easier than ever to contribute to Drupal via code.

This article will explain the steps involved in this workflow. This article will even be more helpful to those who want to get started with code contribution. This is because now one requires very less technical setup on their local to start contribution.

If you wish to watch the workflow in action, I’ve created a video also for learning purpose attached below.

<iframe width="560" height="315" src="https://www.youtube.com/embed/nlA51s_iAXU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Let’s start.

**Step 1: Find a Drupal.org issue OR Create one.**

The first step is to pick an issue or if you intend to create one then go ahead. Next, keep the issue page open.

![](/assets/images/1__ModwQr__tPbzMj__FEHvIYwA.png)

**Step 2: Create Fork.**

Once we know where and what to fix. We can then click the “Create Issue Fork” button in the issue queue and wait for the issue branch to get created. Once created. Click on the branch name. You will be redirected to Drupal Gitlab Interface.

![](/assets/images/1__D2P2k77TDamUqMicYb0Yrw.png)

**Step 3: Make changes to the fork.**

Browse the repository and make changes to all the respective files. Once done scroll down and add a commit message and create a commit to the issue target branch as shown below.

![](/assets/images/1__pIq2yFFMClC4x8w__Gkv4Jg.png)

**Step 4: Commit & Push changes to the issue fork branch.**

Once the changes are merged into the issue branch. You should be able to see a Create Merge Request button on the GitLab interface. When submitting a merge request, make sure the source branch is your issue branch and the target branch should be the intended branch where this change should go.

Review the changes done and hit Submit Merge Request. Your merge request will look something like this.

![](/assets/images/1__uhm9wPmHz____nvnTH1at9CA.png)

Once the MR is submitted, the same is reflected in the Drupal.org issue.

![](/assets/images/1__Z2F9WkPX5q5aiUAq4798Fw.png)

If you add any comment to the MR, the same comment gets synced to the issue as well, so that no communication is lost during the reviews.

![](/assets/images/1__B210Qk8__OFWJiHUQcv8jWQ.png)
![](/assets/images/1__Ah__LK1____F62KG__hckfr1VA.png)

Mark the issue as Needs Review and let the reviewers and maintainers take this issue forward from here.

**How a maintainer can merge a Merge Request?**

Whenever a maintainer opens any issue for their projects. They should see a new select dropdown listing all the open Merge Requests for this current issue.

![](/assets/images/1__WKg2cErGuNRs6T0lMd__yRA.png)

Select the desired MR to merge and click the “Merge” button on the right side to merge the code to the project.

Once the code is merged, a merge comment is created on the issue.

![](/assets/images/1__UIDx5tBvQDDEwNnFK6KPkA.png)

And… we are done.

Notice we just worked on our Browser to create simple contribution like this(watch the video shared above for the above steps in action). This workflow clearly reduces the tools required.

If you are a seasoned contributor and wants to commit & push code by the terminal, you can easily do it by doing the same things shared above but with your terminal. Goto the issue page and click “Show commands” to see all the git URLs for issue forks and the branch created.

![](/assets/images/1__WgxshThnTCh__VXsDiVXwOQ.png)

### Conclusion

I personally feel this was a very long-awaited requirement for the Drupal community. The community has been using the patch workflow ever since and now I feel it is good to have a development workflow similar to how rest of the world does it. This workflow in itself is unique. I liked the way how comments are synced across merge requests and Drupal.org issues.

This IMO will definitely increase Drupal adoption from new contributors and the ones who are outside of Drupal bubble. I see this as a very positive development and looking forward to actively use this for my projects.

Please feel free to [Tweet](https://twitter.com/JayKandari) me about any issues/feedback for this post.

**#DrupalThanks**

See you again!

### References:

*   [About issue forks](https://www.drupal.org/drupalorg/docs/gitlab-integration/issue-forks-merge-requests)
*   [Drupal.org GitLab Merge Request Demo](https://www.youtube.com/watch?v=NIWCXE-aM6Y&ab_channel=DrupalAssociation)
