# Rath

[![kanaries data](https://img.shields.io/twitter/follow/kanaries_data?style=social)](https://twitter.com/kanaries_data)

![](https://img.shields.io/badge/license-AGPL-brightgreen)
![](https://img.shields.io/github/stars/kanaries/rath?color=%23ff85c0)
![](https://img.shields.io/github/workflow/status/kanaries/rath/Rath%20Auto%20Build)
![](https://img.shields.io/npm/v/@kanaries/graphic-walker/latest?label=%40kanaries%2Fgraphic-walker)


<img src="https://kanaries.cn/assets/kanaries-logo.png" alt="logo" width="180px" style="" />

RATH is an OpenSource automated data exploration tool that can help you automate discovery patterns and insights and generate charts and dashboards from multi-dimensional data. It uses an AI-enhanced engine to automate the working flow in data analysis. You can regard RATH as a copilot in data analysis.

 It is not only an open source replacement of tableau but a version with more automation power, including auto insights discovery, predictive interaction, and visual recommendation.

+ Try RATH [here](https://rath.kanaries.net)
+ visit our official website[kanaries website](https://kanaries.net)
+ [🚀 Quick View of RATH's Exploratory Data Analysis](https://medium.com/@observedobserver/quick-view-of-raths-exploratory-data-analysis-65c71866eca5)

## Introduction

Rath is an auto EDA tool (or Augmented Analytic BI), which automates exploring your dataset and discovering interesting patterns and relations, recommending expressiveness and effective visualizations.

Rath provides a different level of automation for different scenarios and users. For instance, the 'MegaAutomation' module provides full automation. Connect your data, and click 'analysis'. Rath will do all the exploration and analysis work for you. Rath will find some insights and patterns in data and generate charts/dashboards for you. The 'SemiAutomation' module is a semi-automation analysis system that can be controlled to focus on your thoughts more. 'Manual Exploration' module is a manual data analysis and visualization tool for whom with specific analysis purpose.

Rath can auto-generate high-dimensional visualization containing complex patterns, while most other auto-EDA tools only provide simple low-dimensional charts with basic statistics patterns. Its means you can use Rath to explore the data to a deep level and find more insights.

Here are the main parts of Rath,

### DataSource
DataSource board is for data uploading, sampling(currently support stream data, which means there is no limit on the size of the file you uploaded), cleaning, and defining fields type(dimensions, measures). In visual insights, we regard dimensions as independent variables or features and measures as dependent variables or targets.

![dataSource-en.png](https://ch-resources.oss-cn-shanghai.aliyuncs.com/images/rath/1.0.0/rath-datasource-01.png)

![dataSource-filter-en.png](https://ch-resources.oss-cn-shanghai.aliyuncs.com/images/rath/1.0.0/datasource-02.png)

### Mega Automation

Rath automates exploring your dataset and discovering interesting patterns, and relations, recommending expressiveness and effective visualizations.
![gallery.png](https://ch-resources.oss-cn-shanghai.aliyuncs.com/images/rath/1.0.0/rath-mega-auto-01.png)

If some of the recommendations catch your interest, you can click the associate button, and Rath will associate more related insights for you.

![gallery-asso](https://ch-resources.oss-cn-shanghai.aliyuncs.com/images/rath/1.0.0/rath-asso-01.png)

If you have some very specific target, you can switch to a manual EDA tool inside Rath called Graphic Walker.

### Manual Exploration
Graphic Walker is a lite tableau/polaris style visual analysis app, which is also based on Wilkinson's Grammer of Graphics. It is used for cases when users have specific analytic targets or want to analyze further results based on the recommended results by Rath's auto insights.

![graphic-walker.png](https://ch-resources.oss-cn-shanghai.aliyuncs.com/images/rath/1.0.0/rath-gw-01.png)

We use similar visualization specification rules in polaris, which is friendly to users who are familiar with tableau.

![graphic-waler.png](https://ch-resources.oss-cn-shanghai.aliyuncs.com/images/rath/1.0.0/rath-gw-02.png)

Manual Exploration is an independent embedding module. You can use it independently in your own app. See more details in `packages/graphic-walker/README.md`

```bash
yarn add @kanaries/graphic-walker
# or

npm i --save @kanaries/graphic-walker
```

### SemiAutomation
Discovery or knowledge build module is a semi-automated data exploration system. It automates step by step and tries to understand what the users are thinking in real-time. Users can tell Rath what they are more interested in and Rath will focus more on the subset user care about.

![semi-auto](https://ch-resources.oss-cn-shanghai.aliyuncs.com/images/rath/1.0.0/rath-semi-02.png)

![discovery](https://ch-resources.oss-cn-shanghai.aliyuncs.com/images/rath/1.0.0/rath-semi-01.png)



### Dashboard
Generate interactive dashboards for yours. Rath will figure out sets of visualizations of which contents are connected to each other and can be used to analyze a specific problem.

You can also specify parts of the dashboard, and RATH
will figure out the best fits for the rest of the dashboard.

### Notebook (deprecated)
Notebook is a board for the user to know what happened in the automatic analysis process and how RATH uses visual-insights. It shows how decisions are made by the application and provide an interactive interface to adjust some of the parameters and operators used by the algorithm.

### Explainer (deprecated)
Explainer uses several insight discovery algorithms to detect what the specific insight type is shown in a visualization recommended. Explainer is an extension of B. Tang's Top K insight paper[4].


You can also use Graphic Walker as a lite tableau style analysis app independently. It can be used as an independent app or an embedding module.

more details can be found in README.md in graphic-walker folder.

## Docs
+ [docs](https://kanaries.net)



## Usage

### Try it
+ on Github Pages(Stable version) [App](https://kanaries.github.io/Rath/)
+ on Kanaries Website [App](https://kanaries.net/)

### Download Desktop Version
- [MacOS](https://ch-resources.oss-cn-shanghai.aliyuncs.com/downloads/rath/Kanaries%20Rath-0.1.0.dmg)
- [Windows](https://ch-resources.oss-cn-shanghai.aliyuncs.com/downloads/rath/Kanaries%20Rath-0.1.0-win.zip)

### deploy

Rath now runs all the computation tasks on webworker. For some large datasets, Rath will use indexedDB to avoid too much memory cost of browsers. For larger datasets (>100MB), Rath can put some of its computation to computation engine support SQL query(such as clickhouse). If you are interested in a server version, check the older version or contact us.

#### deploy connector service
RATH requires a database connector to connect common databases. You need to deploy `apps/connector` and then you can connect a number of common databases as datasource.

#### OLAP Service
Connector service is used as a pure datasource, RATH fetches the data from the bases and loads them into memory.

For larger datasets, or if you can access a high performance OLAP service (such as a clusters of clickhouse). You can start `packages/connectors` which is a OLAP service connector. Not only will it fecthes data from OLAP, but use it as a computation engine as well. RATH
 will push SQL query to the OLAP services instead of computate those tasks in its own engine.


## Documentation
+ [🚀 Quick View of RATH's Exploratory Data Analysis](https://medium.com/@observedobserver/quick-view-of-raths-exploratory-data-analysis-65c71866eca5)

## LICENSE (AGPL)
Rath is an automated data analysis and visualization tool (auto-EDA).

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as
published by the Free Software Foundation, either version 3 of the
License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
