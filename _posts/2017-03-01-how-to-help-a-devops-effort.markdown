---
layout: post
title: "How to help a DevOps effort"
date: 2017-03-01 09:02:20 -0500
categories: 
---
This is some role-specific guidance on how to help a DevOps effort.

### Everyone

Understand continuous delivery and the benefits that can accrue to companies that implement its tenets. "DevOps efforts" fail in many companies because of organizational and cultural challenges, so we need all the help we can get!

Often, when you have a task to do, there are two options:

1. Do it as fast as possible
2. Do it in such a way that neither your nor anyone else ever has to do it again

Think carefully before selecting the first option.

### QA

Automate tests, so we can leverage past work in future release cycles and decrease overall cycle time, since testing time can often be a significant subset of overall cycle time. Focus on eliminating false positives to keep the Deployment pipeline running smoothly; when automated tests fail when there is no bug, we can't rely on them.

### Developers

Write automated tests to prove that your code works. Experiment with writing them before you write your code. Strive to not introduce defects. Catching defects early in the change process (as you write the code) saves significant time, since you (or your colleague who is further handicapped by not having written the code) will have to fix the defect anyway, but you will not have as much of the relevant context in your head after a significant time delay. Think about the deployability of the code you are writing. Maintain backwards compatibility.

### Ops

Automate everything. Prioritize higher-value automation work and refuse to perform manual processes where appropriate. Your time is way too valuable for babysitting manual processes. The automation work will not run out any time soon, it will look way better on your resume, and unblocking your colleagues with automation is a force multiplier. You'll know you're winning when the tools you support and maintain allow your internal stakeholders to do everything they need without needing you to unblock them. Provide advice to your colleagues on improving the overall process quickly and while minimizing risk. Then implement it yourself when they’re busy automating something else. Trust your colleagues to do the right thing and try not to overindex on the downside risk of someone intentionally or inadvertently breaking something because of a change. Increase the transparency and auditability of changes to mitigate the risk of change. The risk of not changing anything can be higher, since we can't continue to generate value in a competitive environment without change.

### Product Managers

Support the improvement of our software development lifecycle by giving the developers and QA people on your team time to improve our applications and tools. Prioritize and support tech debt reduction efforts.

Where possible, set business targets for the team to optimize over specifying how to achieve the goals. 

Plan for and follow through on measuring changes to determine whether business feature requests have the intended effect. If they don’t have the intended effect, consider making another change to try to figure out why. If the changes still don’t have the desired effect, have enough emotional detachment from the change to completely back it out and move on to another change that might work better. Expect this entire cycle to happen fast and work with the engineering team to find ways to make this so.

### Project Managers and Senior Managers

Be aware that implementing best practices in the DevOps space--such as continuous delivery--require fundamental changes to our processes. This change cannot happen without your support. Work to get everyone access to everything they need in their role and in their aspirational roles. Make it a rare occurrence that someone needs to ask for access to something. Mitigate the risks of access with training, change tracking, and transparency. We can actually ship software faster and with less risk and have happier employees and customers. Continuous delivery is happening at Google, Facebook, Amazon, Thoughtworks, ING Group, and LinkedIn. With your support, and if we can together navigate the waters of fairly significant cultural change, it will happen here too.
