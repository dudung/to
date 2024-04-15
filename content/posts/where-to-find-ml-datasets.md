+++
title = 'where to find ml datasets'
date = 2024-04-14T21:42:00+07:00
draft = false
math = true
tags = ['machine learning', 'datasets']
url = '0010'
authors = ['viridi']
+++
Finding machine learning datasets <!--more-->


## intro
One of the challenges in entering machine learning (ML) world is to find the right datasets [^ailinkedin_2024]. Since it is a very important aspect, a university even provides information about it, e.g. on library website [^lan_2024]. And there are many posts, stories, articles about how to find them, e.g. list of datasets sources [^badr_2019][^hillier_2023][^luck_2021] or already grouped in categories [^gupta_2022][^rizzoli_2021], that can be found.

Once websites for datasets can be found, the datasets themselves might not easy to obtain as files in CSV, XLSX, or other formats. They can be still in raw format that must be first transformed, at least, to flat file in order to be used as dataset.

Some experiences in searching data are given in this post and processes to transform them as datasets are also suggested.


## etl
ETL, is an initialism [^turkel_2023], that stands for extract, transform, and load, which is a process to integrate data into a data warehouse in providing a reliable single source of truth (SSOT) necessary for business intelligence (BI) and various other needs, such as storage, data analytics, and machine learning [^haider_2024].

The ETL is a three-step process.

+ Data extraction
  - Extract raw data from relevant data sources, e.g. databases, files, etc.
  - Stored extracted data in landing zone called staging area temporarily.
+ Data transformation
  - Transform stored data in staging area to meet some required standards, e.g. perform data cleansing, data deduplication, joins & tree joins, normalization & de-normalization, merge, etc to maintain data integrity.
  - Store transformed data in staging area temporarily.
+ Data loading
  - Load transformed data from staging area to permanent storage system, e.g. a data warehouse, as well-structured data.

Normally, ETL is an automated process, but in this post it will be conducted manually a learning process.


## notes
[^ailinkedin_2024]: AI and the LinkedIn community, "You need to build a machine learning model. How can you find the right data set?", LinkedIn, 11 Jan 2024, url https://www.linkedin.com/advice/0/you-need-build-machine-learning-model-how-can-find-right-djtpc [20240414].
[^lan_2024]: Haoyong Lan, "Artificial Intelligence: Find Datasets", Carnegie Mellon University Libraries, 15 Jan 2024, url https://guides.library.cmu.edu/machine-learning [20240414].
[^badr_2019]: Will Badr, "Top Sources For Machine Learning Datasets", Towards Data Science -- Medium, 13 Jan 2019, url https://medium.com/p/bb6d0dc3378b [20240414].
[^gupta_2022]: Satish Chandra Gupta, "50 Public Datasets for Machine Learning Projects", ML4Devs, 7 Jul 2022, url https://www.ml4devs.com/articles/datasets-for-machine-learning-and-data-science/ [20240414].
[^haider_2024]: Khurram Haider, "What is ETL? – Extract, Transform, Load Explained", Astera, 25 Mar 2024, url https://www.astera.com/type/blog/etl/ [20240415].
[^hillier_2023]: Will Hillier, "10 Great Places to Find Free Datasets for Your Next Project", CareerFoundry Blog, 9 Nov 2023, url https://careerfoundry.com/en/blog/data-analytics/where-to-find-free-datasets/ [20240414].
[^luck_2021]: Sandro Luck, "9 Best Places To Find Machine Learning Datasets", Towards Data Science -- Medium, 9 Feb 2021, url https://medium.com/p/dfdba8af5220 [20240414].
[^rizzoli_2021]: Alberto Rizzoli, "65+ Best Free Datasets for Machine Learning", V7Labs, 1 Jun 2021, url https://www.v7labs.com/blog/best-free-datasets-for-machine-learning [20240414].
[^turkel_2023]: Lucie Turkel, "Acronym vs. Abbreviation vs. Initialism: What’s the Difference?", Reader's Digest, 6 Feb 2023, url https://www.rd.com/article/acronym-vs-abbreviation-whats-the-difference/ [20240415].
