# Towards Real-Time Flood Prediction Models Using Crowdsourced Information

<!-- > GFM  Markdown and WYSIWYG Editor - Productive and Extensible -->

<!-- [![github release version](https://img.shields.io/github/v/release/nhn/tui.editor.svg?include_prereleases)](https://github.com/nhn/tui.editor/releases/latest) [![npm version](https://img.shields.io/npm/v/@toast-ui/editor.svg)](https://www.npmjs.com/package/@toast-ui/editor) [![license](https://img.shields.io/github/license/nhn/tui.editor.svg)](https://github.com/nhn/tui.editor/blob/master/LICENSE) [![PRs welcome](https://img.shields.io/badge/PRs-welcome-ff69b4.svg)](https://github.com/nhn/tui.editor/issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22) [![code with hearth by NHN Cloud](https://img.shields.io/badge/%3C%2F%3E%20with%20%E2%99%A5%20by-NHN_Cloud-ff1414.svg)](https://github.com/nhn) -->

<img src="https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/method.jpg?raw=true" />


## 🚩 Table of Contents

<!-- - [Packages](#-packages) -->
- [Why Crowdsourced Information?](#-why-crowdsourced-information)
- [Why Bayesian Neuro Network?](#-why-bayesian-neuro-network)
- [1st Round Results](#-1st-round-results)
- [2nd Round Results](#-2nd-round-results)
- [Proof of Generalizability](#-proof-of-generalizability)
- [Limitations](#-limitations)
- [Highlights](#-highlights)
- [Author](#-author)
<!-- - [License](#-license) -->


<!-- ## 📦 Packages

### TOAST UI Editor

| Name | Description |
| --- | --- |
| [`@toast-ui/editor`](https://github.com/nhn/tui.editor/tree/master/apps/editor) | Plain JavaScript component |

### TOAST UI Editor's Wrappers

| Name | Description |
| --- | --- |
| [`@toast-ui/react-editor`](https://github.com/nhn/tui.editor/tree/master/apps/react-editor) | [React](https://reactjs.org/) wrapper component |
| [`@toast-ui/vue-editor`](https://github.com/nhn/tui.editor/tree/master/apps/vue-editor) | [Vue](https://vuejs.org/) wrapper component |

### TOAST UI Editor's Plugins

| Name | Description |
| --- | --- |
| [`@toast-ui/editor-plugin-chart`](https://github.com/nhn/tui.editor/tree/master/plugins/chart) | Plugin to render chart |
| [`@toast-ui/editor-plugin-code-syntax-highlight`](https://github.com/nhn/tui.editor/tree/master/plugins/code-syntax-highlight) | Plugin to highlight code syntax |
| [`@toast-ui/editor-plugin-color-syntax`](https://github.com/nhn/tui.editor/tree/master/plugins/color-syntax) | Plugin to color editing text |
| [`@toast-ui/editor-plugin-table-merged-cell`](https://github.com/nhn/tui.editor/tree/master/plugins/table-merged-cell) | Plugin to merge table columns |
| [`@toast-ui/editor-plugin-uml`](https://github.com/nhn/tui.editor/tree/master/plugins/uml) | Plugin to render UML | -->


## 🤖 Why Crowdsourced Information?

Scholars have valued monitoring flooding reports on social media to reveal flood propagation for the past 10 years. More recently, they have incorporated predictors such as topographic and land cover features, precipitation, and others, exploring the relationship between these predictors and **not only** flooded **but also** unflooded spots using machine learning. This allows them to map flood risk for an entire region, including areas with limited flood reports.

However, scholars have solely relied on social media reports or their personal experiences (when studying flood risk in their hometowns). No one has yet reached out to local communities to gather more localized knowledge about flooded and unflooded areas. 

**So... WE DID!** 

Our goal is to create a flood risk map for Pinellas County using similar predictors as mentioned above. We need information on both flooded and unflooded areas. It is not difficult to find flood reports online though it requires diligent manual effort these days. The most chanllenging part is identifying areas that are not flooded. **So we reached out to local neighbors in Pinellas County, and they responded with great kindness.** They also helped us geocode some "flooded images" as well!

<!-- ### Productive Markdown Mode

![markdown](https://user-images.githubusercontent.com/37766175/121464762-71e2fc80-c9ef-11eb-9a0a-7b06e08d3ccb.png)

**CommonMark + GFM Specifications**

Today *CommonMark* is the de-facto *Markdown* standard. *GFM (GitHub Flavored Markdown)* is another popular specification based on *CommonMark* - maintained by *GitHub*, which is the *Markdown* mostly used. TOAST UI Editor follows both [*CommonMark*](http://commonmark.org/) and [*GFM*](https://github.github.com/gfm/) specifications. Write documents with ease using productive tools provided by TOAST UI Editor and you can easily open the produced document wherever the specifications are supported.

* **Live Preview** : Edit Markdown while keeping an eye on the rendered HTML. Your edits will be applied immediately.
* **Scroll Sync** : Synchronous scrolling between Markdown and Preview. You don't need to scroll through each one separately.
* **Syntax Highlight** : You can check broken Markdown syntax immediately.

### Easy WYSIWYG Mode

![wysiwyg](https://user-images.githubusercontent.com/37766175/121808381-251f5000-cc93-11eb-8c47-4f5a809de2b3.png)

* **Table** : Through the context menu of the table, you can add or delete columns or rows of the table, and you can also arrange text in cells.
* **Custom Block Editor** : The custom block area can be edited through the internal editor.
* **Copy and Paste** : Paste anything from browser, screenshot, excel, powerpoint, etc.

### UI
* **Toolbar** : Through the toolbar, you can style or add elements to the document you are editing.
![UI](https://user-images.githubusercontent.com/37766175/121808231-767b0f80-cc92-11eb-82a0-433123746982.png)

* **Dark Theme** : You can use the dark theme.
![UI](https://user-images.githubusercontent.com/37766175/121808649-8136a400-cc94-11eb-8674-812e170ccab5.png)

### Use of Various Extended Functions - Plugins

![plugin](https://user-images.githubusercontent.com/37766175/121808323-d8d41000-cc92-11eb-9117-b92a435c9b43.png)

CommonMark and GFM are great, but we often need more abstraction. The TOAST UI Editor comes with powerful **Plugins** in compliance with the Markdown syntax.

**Five basic plugins** are provided as follows, and can be downloaded and used with npm.

* [**`chart`**](https://github.com/nhn/tui.editor/tree/master/plugins/chart) : A code block marked as a 'chart' will render [TOAST UI Chart](https://github.com/nhn/tui.chart).
* [**`code-syntax-highlight`**](https://github.com/nhn/tui.editor/tree/master/plugins/code-syntax-highlight) : Highlight the code block area corresponding to the language provided by [Prism.js](https://prismjs.com/).
* [**`color-syntax`**](https://github.com/nhn/tui.editor/tree/master/plugins/color-syntax) : 
Using [TOAST UI ColorPicker](https://github.com/nhn/tui.color-picker), you can change the color of the editing text with the GUI.
* [**`table-merged-cell`**](https://github.com/nhn/tui.editor/tree/master/plugins/table-merged-cell) : 
You can merge columns of the table header and body area.
* [**`uml`**](https://github.com/nhn/tui.editor/tree/master/plugins/uml) : A code block marked as an 'uml' will render [UML diagrams](http://plantuml.com/screenshot). -->

## 🎨 Why Bayesian Neuro Network?
### Planning in the face of incomplete information
<!-- * [Viewer](https://github.com/nhn/tui.editor/tree/master/docs/en/viewer.md) : Supports a mode to display only markdown data without an editing area.
* [Internationalization (i18n)](https://github.com/nhn/tui.editor/tree/master/docs/en/i18n.md) : Supports English, Dutch, Korean, Japanese, Chinese, Spanish, German, Russian, French, Ukrainian, Turkish, Finnish, Czech, Arabic, Polish, Galician, Swedish, Italian, Norwegian, Croatian + language and you can extend.
* [Widget](https://github.com/nhn/tui.editor/tree/master/docs/en/widget.md) : This feature allows you to configure the rules that replaces the string matching to a specific `RegExp` with the widget node.
* [Custom Block](https://github.com/nhn/tui.editor/tree/master/docs/en/custom-block.md) : Nodes not supported by Markdown can be defined through custom block. You can display the node what you want through writing the parsing logic with custom block. -->
![Kirkwood, Charlie, et al., 2022](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/bnn.jpg?raw=true)

We used Monte Carlo Dropout to approximate Bayesian approach. 

* A dropout layer at the very top serves as our prior, allowing the model to only take a subset of information in each simulation. 

* Train a fixed set of weights by maximizing the likelihood.

* Simulate a set of posterior samples by combining prior and likelihood. The trained model takes a subset of information in each simulation to make predictions

* Take the mean value of the entire distribution of posterior predictions to embrace a wide range of possible outcomes.

**Yes, but Why?**
Because... We want to ask the model to mimic the scenario of **Planing in the face of incomplete information**. In planning processes, we rarely have all the information we need; we only have access to subsets of the overall picture, and these subsets constantly change over time. We want our model to make predictions under such conditions so that we can generate a wide range of outcomes for different scenarios and incorporate all of them into our final results.

## 🐾 1st Round Results

<!-- * [Basic](https://nhn.github.io/tui.editor/latest/tutorial-example01-editor-basic)
* [Viewer](https://nhn.github.io/tui.editor/latest/tutorial-example04-viewer)
* [Using All Plugins](https://nhn.github.io/tui.editor/latest/tutorial-example12-editor-with-all-plugins)
* [Creating the User's Plugin](https://nhn.github.io/tui.editor/latest/tutorial-example13-creating-plugin)
* [Customizing the Toobar Buttons](https://nhn.github.io/tui.editor/latest/tutorial-example15-customizing-toolbar-buttons)
* [Internationalization (i18n)](https://nhn.github.io/tui.editor/latest/tutorial-example16-i18n)

Here are more [examples](https://nhn.github.io/tui.editor/latest/tutorial-example01-editor-basic) and play with TOAST UI Editor! -->
We evaulated our model quantitatively and then qualitatively.
* Quantitative Evaluation
![Idalia 1st round training quantitative evaluation](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/idalia1_quant.jpg?raw=true)

* Qualitative Evaluation
![Idalia 1st round training qualitative Evaluation, flooded](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/idalia1_qualitative_flood.jpg?raw=true)

![Idalia 1st round training qualitative Evaluation, not flooded](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/idalia1_qualitative_notflood.jpg?raw=true)

**The model did great jobs in predicting flood risks in most areas, but still...**

* Over alerting predictions after 1st round training
    * Over alerting to "island" neighborhoods
    ![Idalia 1st round training qualitative Evaluation, over alerting to island neighborhoods](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/over_alterting_idalia1.jpg?raw=true)

    * Over alerting due to modeler's over alerting interpretation
    ![Idalia 1st round training qualitative Evaluation, over alerting due to over alerting interpretation](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/over_interpret2alterting_idalia1.jpg?raw=true)

## 🔧 2nd Round Results
After verifying the results of our first-round training with neighbors in Pinellas County, we realized the need to update our interpretation of their messages and revise the training dataset to regularize the model's predictions. 
![Idalia 2nd round training, dataset revision](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/training_ds_revise_idalia2.jpg?raw=true)

Again, we evaluated our model quantitatively then qualitatively. Overall, the model performed well, and the over-alerting 'false positives' from the first-round predictions were corrected in the second round.
![Idalia 2nd round training, corrected false positives](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/corrected_results_idalia2.jpg?raw=true)

<!-- | <img src="https://user-images.githubusercontent.com/1215767/34348387-a2e64588-ea4d-11e7-8267-a43365103afe.png" alt="Chrome" width="16px" height="16px" /> Chrome | <img src="https://user-images.githubusercontent.com/1215767/34348590-250b3ca2-ea4f-11e7-9efb-da953359321f.png" alt="IE" width="16px" height="16px" /> Internet Explorer | <img src="https://user-images.githubusercontent.com/1215767/34348380-93e77ae8-ea4d-11e7-8696-9a989ddbbbf5.png" alt="Edge" width="16px" height="16px" /> Edge | <img src="https://user-images.githubusercontent.com/1215767/34348394-a981f892-ea4d-11e7-9156-d128d58386b9.png" alt="Safari" width="16px" height="16px" /> Safari | <img src="https://user-images.githubusercontent.com/1215767/34348383-9e7ed492-ea4d-11e7-910c-03b39d52f496.png" alt="Firefox" width="16px" height="16px" /> Firefox |
| :---------: | :---------: | :---------: | :---------: | :---------: |
| Yes | 11+ | Yes | Yes | Yes | -->


## 🌏 Proof of Generalizability
We applied the same data collection procedure and prediction method to assess flood risk for another storm surge event on December 17, 2023, in Pinellas County, and it performed quite well.
<!-- TOAST UI products are open source, so you can create a pull request(PR) after you fix issues. Run npm scripts and develop yourself with the following process.

### Setup

Fork `main` branch into your personal repository. Clone it to local computer. Install node modules. Before starting development, you should check if there are any errors.

```sh
$ git clone https://github.com/{your-personal-repo}/tui.editor.git
$ npm install
$ npm run build toastmark
$ npm run test editor
```

> TOAST UI Editor uses [npm workspace](https://docs.npmjs.com/cli/v7/using-npm/workspaces/), so you need to set the environment based on [npm7](https://github.blog/2021-02-02-npm-7-is-now-generally-available/). If subversion is used, dependencies must be installed by moving direct paths per package.

### Develop

You can see your code reflected as soon as you save the code by running a server. Don't miss adding test cases and then make green rights.

#### Run snowpack-dev-server
[snowpack](https://www.snowpack.dev/) allows you to run a development server without bundling.

``` sh
$ npm run serve editor
```

#### Run webpack-dev-server
If testing of legacy browsers is required, the development server can still be run using a [webpack](https://webpack.js.org/).

``` sh
$ npm run serve:ie editor
```

#### Run test

``` sh
$ npm test editor
```

### Pull Request

Before uploading your PR, run test one last time to check if there are any errors. If it has no errors, commit and then push it!

For more information on PR's steps, please see links in the Contributing section. -->

## 💬 Limitations
However, the model still has some limitations. For instance, in very small neighborhoods with mixed flood risks during an event, the model tends to predict the entire neighborhood as having a high flood risk.
![limitations_in_predict_flood_risk_in_small_neighborhoods](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/Limitation.jpg?raw=true)

Although the model does not make flawless predictions, over-alerting at an appropriate scale is harmless because our goal is to indicate that the neighborhood is impacted during the storm.

**Plus, this limitation is rather an opportunity to encourage modelers to to engage more closely with communities to gather more detailed information. With finer data in the training dataset, the model can achieve more accurate predictions at a finer resolution.**

<!-- * [Code of Conduct](https://github.com/nhn/tui.editor/blob/master/CODE_OF_CONDUCT.md)
* [Contributing Guideline](https://github.com/nhn/tui.editor/blob/master/CONTRIBUTING.md)
* [Commit Convention](https://github.com/nhn/tui.editor/blob/master/docs/COMMIT_MESSAGE_CONVENTION.md)
* [Issue Guidelines](https://github.com/nhn/tui.editor/tree/master/.github/ISSUE_TEMPLATE) -->


## 🍞 Highlights
**Our model is a bridge between flood prediction modelers and the communities. We encouraged collaborative planning!**
![project_highlights](https://github.com/GT-CURA/Flood_Prediction_BNN_Pinellas_FL/blob/main/img/highlights.jpg?raw=true)

- We showed how to improve the model performance by adjusting the training dataset, IF NECESSARY

- We employed the Bayesian Framework to mimic “Planning in the face of incomplete information”

- We know this modeling approach is still quite prototyping and far from perfect. However, **THE most important contribution** of our work is, it builds a communication bridge between flood prediction modelers and the communities. It encourage modelers to take the initiative to reach out to communities instead of passively monitoring the social media activities behind the scene do the flood prediction just on their own.

<!-- - [TOAST UI Calendar](https://github.com/nhn/tui.calendar)
- [TOAST UI Chart](https://github.com/nhn/tui.chart)
- [TOAST UI Grid](https://github.com/nhn/tui.grid)
- [TOAST UI Image Editor](https://github.com/nhn/tui.image-editor)
- [TOAST UI Components](https://github.com/nhn) -->


## 🚀 Author
Patty(Mengjue) Zhu (mzhu356@gatech.edu)
Subhrajit Guhathakurta (subhro.guha@design.gatech.edu)
Barnali Dixon (bdixon@usf.edu)
<!-- * [NHN Dooray! - Collaboration Service (Project, Messenger, Mail, Calendar, Drive, Wiki, Contacts)](https://dooray.com)
* [UNOTES - Visual Studio Code Extension](https://marketplace.visualstudio.com/items?itemName=ryanmcalister.Unotes) -->


<!-- ## 📜 License

This software is licensed under the [MIT](https://github.com/nhn/tui.editor/blob/master/LICENSE) © [NHN Cloud](https://github.com/nhn). -->
