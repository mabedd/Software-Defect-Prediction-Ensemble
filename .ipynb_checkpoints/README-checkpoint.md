<img src='https://d3v77cxrhim28u.cloudfront.net/wp-content/uploads/2018/11/bg_img_1.png'>

# Software Defect Prediction using Ensemble Learning on Selected Features
<h2><strong><italic>Research Paper Implementation</italic></strong></h2>
A comprehensive implementation of the paper <a href='https://www.sciencedirect.com/science/article/abs/pii/S0950584914001591'>Software defect prediction using ensemble learning on selected features.</a>

The paper was presented by <strong>Dr.Lahouari Ghouti</strong> at Prince Sultan Univserity in the Software Analytics course (SE480).

The implementation was benchmarked on the <a href='https://figshare.com/articles/dataset/Software_Defect_Prediction_Dataset/13536506/1'>Ant 1.7</a> public dataset for software metrics. According to the paper this particular dataset achieved the highest performance with the proposed APE.

# Table of contents
- [Software Defect Prediction using Ensemble Learning on Selected Features](#software-defect-prediction-using-ensemble-learning-on-selected-features)
- [Table of contents](#table-of-contents)
- [Approach](#approach)
    - [Used Models](#used-models)
    - [Training Pipeline](#training-pipeline)
    - [Solve Class Imbalance](#solve-class-imbalance)
    - [Individual Results](#individual-results)
    - [Average Probability Estimator](#average-probability-estimator)
- [Conclusion](#conclusion)
- [Contribute](#contribute)

# Approach

After adding the extension to Chrome/Firefox, it will light-up every time you load a compatible website.

When a page is loaded, the extension would hide all the images in the page and only show images that have been classified as **NOT NSFW**.

You can toggle(off/on) the extension from the ```chrome://extensions``` page in Chrome and ```about:debugging#/runtime/this-firefox``` in Firefox.

Open popup window to change NSFW Filter settings

<table>
  <tr>
    <td vlign="center">
      <img src="./demo/images/pin_popup.png" alt="Pin popup window">
    </td>
    <td vlign="center">
      <img src="./demo/images/popup.png" alt="Popup window">
    </td>
  </tr>
</table>

### Used Models

To install the developer version follow the steps below. To just use the extension download from [**chrome.google.com/webstore/nsfw-filter**](https://chrome.google.com/webstore/detail/nsfw-filter/kmgagnlkckiamnenbpigfaljmanlbbhh)

To run development version in clean environment use command:

```sh
npm run dev:chrome
```

Or open Google Chrome and open the Extension Management page by navigating to ```chrome://extensions``` or by opening Settings and clicking Extensions from the bottom left.

Enable Developer Mode by clicking the toggle switch next to Developer mode.

Click the "Load Unpacked" button and select the extension directory(```.../dist```).

<p align="center">
  <img src="./demo/images/install_instructions.png" alt="Install Instructions">
<p/>

Voila! The extension is now installed and ready to be used!

### Training Pipeline

To install the developer version follow the steps below. To just use the extension download from [**addons.mozilla/nsfw-filter**](https://addons.mozilla.org/en-US/firefox/addon/nsfw-filter/)

To run development version in clean environment use command:

```sh
npm run dev:firefox
```

Or open Firefox and open the Debug Add-ons page by navigating to ```about:debugging#/runtime/this-firefox``` or by selecting it from Settings dropdown in the add-ons page.

Click Load Temporary Add-on and select the ```manifest.json``` file from the ```.../dist``` directory.

<p align="center">
  <img src="./demo/images/install_instructions_firefox.png" width="470px" alt="Install Instructions">
<p/>

### Solve Class Imbalance
### Individual Results
### Average Probability Estimator


# Conclusion

That's it! The extension is now ready to be used in Firefox!
<!--
### Activity Diagram

![](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/nsfw-filter/nsfw-filter/master/demo/UML/activity-diagram.plantuml)
-->
# Contribute

Please check the [**Contributing Guidelines**](https://github.com/navendu-pottekkat/nsfw-filter/blob/master/.github/markdown/CONTRIBUTING.md) before contributing.

You can also sponsor on [**Open Collective**](https://opencollective.com/nsfwfilter/donate) or [**become a Patron**](https://www.patreon.com/bePatron?u=41162696).

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/YegorZaremba"><img src="https://avatars3.githubusercontent.com/u/31797554?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Yegor <3</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/commits?author=YegorZaremba" title="Code">💻</a> <a href="#design-YegorZaremba" title="Design">🎨</a> <a href="#ideas-YegorZaremba" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="http://navendu.me"><img src="https://avatars1.githubusercontent.com/u/49474499?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Navendu Pottekkat</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/commits?author=navendu-pottekkat" title="Code">💻</a> <a href="#content-navendu-pottekkat" title="Content">🖋</a> <a href="https://github.com/nsfw-filter/nsfw-filter/commits?author=navendu-pottekkat" title="Documentation">📖</a> <a href="#design-navendu-pottekkat" title="Design">🎨</a> <a href="#ideas-navendu-pottekkat" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://github.com/anonacc"><img src="https://avatars3.githubusercontent.com/u/64102225?v=4?s=100" width="100px;" alt=""/><br /><sub><b>anonacc</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Aanonacc" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/abhirammltr"><img src="https://avatars1.githubusercontent.com/u/32649851?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Abhiram V V</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/commits?author=abhirammltr" title="Code">💻</a> <a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Aabhirammltr" title="Bug reports">🐛</a> <a href="#ideas-abhirammltr" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://github.com/yxlin118"><img src="https://avatars1.githubusercontent.com/u/54916304?v=4?s=100" width="100px;" alt=""/><br /><sub><b>yxlin118</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Ayxlin118" title="Bug reports">🐛</a> <a href="#ideas-yxlin118" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://clay.sh"><img src="https://avatars3.githubusercontent.com/u/16675291?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Clay McGinnis</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/pulls?q=is%3Apr+reviewed-by%3AClayMav" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="https://www.youtube.com/channel/UCPGv2tVqEt6iBFnnMTjnRBA"><img src="https://avatars1.githubusercontent.com/u/6668371?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Brady Dowling</b></sub></a><br /><a href="#ideas-bradydowling" title="Ideas, Planning, & Feedback">🤔</a></td>
  </tr>
  <tr>
    <td align="center"><a href="http://littlebluelabs.com"><img src="https://avatars2.githubusercontent.com/u/32261?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Mike Crittenden</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/commits?author=mikecrittenden" title="Documentation">📖</a></td>
    <td align="center"><a href="https://github.com/garfieldbanks"><img src="https://avatars3.githubusercontent.com/u/12904270?v=4?s=100" width="100px;" alt=""/><br /><sub><b>garfieldbanks</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Agarfieldbanks" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/TitusRobyK"><img src="https://avatars1.githubusercontent.com/u/32787952?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Titus Roby K</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3ATitusRobyK" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/hsusanoo"><img src="https://avatars2.githubusercontent.com/u/35850056?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Haitam</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Ahsusanoo" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/lizhendong128"><img src="https://avatars3.githubusercontent.com/u/24618122?v=4?s=100" width="100px;" alt=""/><br /><sub><b>lizhendong128</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Alizhendong128" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/Woctor-Dho"><img src="https://avatars3.githubusercontent.com/u/25572322?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Woctor-Dho</b></sub></a><br /><a href="#ideas-Woctor-Dho" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://github.com/miaokun-normal"><img src="https://avatars2.githubusercontent.com/u/67724210?v=4?s=100" width="100px;" alt=""/><br /><sub><b>miaokun-normal</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Amiaokun-normal" title="Bug reports">🐛</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://christopher-bradshaw.com"><img src="https://avatars1.githubusercontent.com/u/1205871?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Christopher Bradshaw</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Akitsune7" title="Bug reports">🐛</a></td>
    <td align="center"><a href="https://github.com/wingman-jr-addon"><img src="https://avatars3.githubusercontent.com/u/55339824?v=4?s=100" width="100px;" alt=""/><br /><sub><b>wingman-jr-addon</b></sub></a><br /><a href="#ideas-wingman-jr-addon" title="Ideas, Planning, & Feedback">🤔</a></td>
    <td align="center"><a href="https://github.com/Andrewrick1"><img src="https://avatars2.githubusercontent.com/u/31154843?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Sagar paul</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/commits?author=Andrewrick1" title="Documentation">📖</a></td>
    <td align="center"><a href="https://github.com/govza"><img src="https://avatars0.githubusercontent.com/u/1425574?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Rasul</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3Agovza" title="Bug reports">🐛</a> <a href="https://github.com/nsfw-filter/nsfw-filter/commits?author=govza" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/Gother01"><img src="https://avatars2.githubusercontent.com/u/65875436?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Aldulkadir Beceri</b></sub></a><br /><a href="https://github.com/nsfw-filter/nsfw-filter/issues?q=author%3AGother01" title="Bug reports">🐛</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!