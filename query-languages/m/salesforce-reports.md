---
title: "Salesforce.Reports | Microsoft Docs"
ms.date: 4/16/2018
ms.prod: power-query
ms.reviewer: owend
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
---
# Salesforce.Reports
<code>Salesforce.Reports(optional **loginUrl** as nullable text, optional **options** as nullable record) as table</code>

## About

Returns the reports on the Salesforce account provided in the credentials. The account will be connected through the provided environment <code>loginUrl</code>. If no environment is provided then the account will connect to production (https://login.salesforce.com). An optional record parameter, <code>options</code>, may be provided to specify additional properties. The record can contain the following fields: <code>ApiVersion</code> : The Salesforce API version to use for this query. When not specified, API version 29.0 is used.
