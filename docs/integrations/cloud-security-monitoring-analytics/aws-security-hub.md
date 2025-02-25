---
id: aws-security-hub
title: Sumo Logic App for AWS Security Hub Cloud Security Monitoring and Analytics
sidebar_label: AWS Security Hub
description: The Sumo Logic AWS Security Hub app is designed to extract key findings from the AWS Security Hub, which is designed to centrally view and manage security alerts and automate security checks.
---

import useBaseUrl from '@docusaurus/useBaseUrl';

<img src={useBaseUrl('img/integrations/amazon-aws/security-hub.png')} alt="Thumbnail icon" width="50"/>

The Sumo Logic AWS Security Hub app is designed to extract key findings from the AWS Security Hub, which is designed to centrally view and manage security alerts and automate security checks. The additional level of analysis within these dashboards surfaces the most relevant findings and takes a focused approach to improve overall security posture. Finding types and severity levels act as leading indicators for security engineers to go into security incidents with the most relevant technical details to address active threats.

## Collecting Findings

To set up Collection, follow the instructions provided at [Collect findings for the AWS Security Hub App](/docs/integrations/amazon-aws/security-hub.md).

## Installing the AWS Security Hub App

Now that you've set up ingested and collected findings for AWS Security Hub, you can install the Sumo Logic App for AWS Security Hub and use the preconfigured searches and [Dashboards](#viewing-aws-security-hub-dashboards) that provide insight into your data.

To install the Sumo Logic App for AWS Security Hub, do the following:

Locate and install the app you need from the **App Catalog**. If you want to see a preview of the dashboards included with the app before installing, click **Preview Dashboards**.

1. From the **App Catalog**, search for and select the app**.**
2. Select the version of the service you're using and click **Add to Library**. Version selection is applicable only to a few apps currently. For more information, see the [Install the Apps from the Library](/docs/get-started/sumo-logic-apps#install-apps-from-the-library).
3. To install the app, complete the following fields.
   * **App Name.** You can retain the existing name, or enter a name of your choice for the app. 
   * **Data Source.** Select either of these options for the data source. 
        * Choose **Source Category**, and select a source category from the list. 
        * Choose **Enter a Custom Data Filter**, and enter a custom source category beginning with an underscore. Example: (`_sourceCategory=MyCategory`). 
   * **Advanced**. Select the **Location in Library** (the default is the Personal folder in the library), or click **New Folder** to add a new folder.
4. Click **Add to Library**.

Once an app is installed, it will appear in your **Personal** folder, or another folder that you specified. From here, you can share it with your organization.

Panels will start to fill automatically. It's important to note that each panel slowly fills with data matching the time range query and received since the panel was created. Results won't immediately be available, but with a bit of time, you'll see full graphs and maps.


## Viewing AWS Security Hub Dashboards

**Each dashboard has a set of filters** that you can apply to the entire dashboard. Click the funnel icon in the top dashboard menu bar to display a scrollable list of filters that narrow search results across the entire dashboard.


### AWS Security Hub - Security Monitoring - Overview

See the overview of Security Hub findings broken down by severity. Filters are available to limit the dashboard panels to specific account IDs, finding IDs, finding types, normalized severity, and title.

<img src={useBaseUrl('img/integrations/cloud-security-monitoring-analytics/AWS-Security-Hub-Security-Monitoring-Overview.png')} alt="AWS Security Hub dashboards" />


#### Findings Summary

**All Security Findings**. See the count of total findings of the last 24 hours by default or the dashboard time window setting.

**Findings by Severity.** Line chart showing the relative volumes of findings over the last 24 hours by default or the dashboard time window setting separated by severity.

**Last 20 Findings**. Provides a table detailing the 20 most recent findings.


#### Critical, High, Medium, Low Severity Findings

All panels for Critical, High, Medium, and Low Severity findings are the same. The only difference is filtering based on the listed severity level.

**Severity Findings**. See the count of findings at this severity over the last 24 hours by default or the dashboard time window setting.

**Severity Outliers**. Review the trending volume of findings at this severity level over the last 24 hours by default or the dashboard time window setting. The gray thresholds show ranges within 3 standard deviations of the past 10 mean values. Pink triangles show values that exceed that threshold and are likely points of investigation considering the large change in volume of findings.

**Last 20 Severity Findings**. See the details of the last 20 findings at this severity level.


### AWS Security Hub - Security Analytics - Compliance

See the overview of Security Hub findings broken down by compliance status. Filters are available to limit the dashboard panels to specific account IDs, finding IDs, finding types, normalized severity, title, and compliance status.

<img src={useBaseUrl('img/integrations/cloud-security-monitoring-analytics/AWS-Security-Hub-Security-Analytics-Compliance.png')} alt="AWS Security Hub dashboards" />


#### Findings Summary

**All Compliance Findings**. See the count of total findings of the last 24 hours by default or the dashboard time window setting.

**Compliance Breakdown.** Line chart showing the relative volumes of findings over the last 24 hours by default or the dashboard time window setting separated by severity. One or more compliance statuses can be filtered by selecting the status from the legend at the bottom of the chart.

**Last 20 Compliance Findings**. Provides a table detailing the 20 most recent findings.


#### Failed, Warning, Not Available, Success, and Passed Findings.  

All panels for each section of findings are the same. The only difference is filtering based on the compliance status.

**Compliance Findings**. See the count of findings at this status over the last 24 hours by default or the dashboard time window setting.

**Severity Outliers**. Review the trending volume of findings at this severity level over the last 24 hours by default or the dashboard time window setting. The gray thresholds show ranges within 3 standard deviations of the past 10 mean values. Pink triangles show values that exceed that threshold and are likely points of investigation considering the large change in volume of findings.

**Last 20 Severity Findings**. See the details of the last 20 findings at this severity level.
