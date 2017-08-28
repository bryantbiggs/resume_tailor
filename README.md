# Resume Tailor

[![Waffle](https://badge.waffle.io/bryantbiggs/resume_tailor.png?label=ready&title=Ready)](https://waffle.io/bryantbiggs/resume_tailor?utm_source=badge)
[![Code Climate](https://codeclimate.com/github/bryantbiggs/resume_tailor/badges/gpa.svg)](https://codeclimate.com/github/bryantbiggs/resume_tailor)
[![Issue Count](https://codeclimate.com/github/bryantbiggs/resume_tailor/badges/issue_count.svg)](https://codeclimate.com/github/bryantbiggs/resume_tailor)
[![Test Coverage](https://codeclimate.com/github/bryantbiggs/resume_tailor/badges/coverage.svg)](https://codeclimate.com/github/bryantbiggs/resume_tailor/coverage)

## Project Description

An unsupervised analysis combining topic modeling and clustering to preserve an individuals work history and credentials while tailoring their resume towards a new career field.

![](static/resume_tailor.jpg)
[Image source](http://www.youtern.com/thesavvyintern/index.php/2016/01/22/heres-how-to-use-job-descriptions-to-tailor-your-resume-infographic/)

---

## Motivation

Currently undergoing a career switch from mechanical engineering into data science and data engineering, I was initially unsure of how to preserve what I had accomplished in my career so far while creating a resume that is targeted towards data science/data engineering roles. Through this project I hope to exchange similar words and phrases within my current resume in order to more closely match those in the data field without removing any prior work experience or accomplishments.

---

# Data Sources

- [Indeed Resume](https://www.indeed.com/resumes) search - inputing select terms (mechanical engineer, data scientist, etc.) will yield search results of individual resumes that fall within that category

---

# Libraries Utilized

- phantomjs, selenium - Spawn a pool of workers to request resumes from Indeed without being flagged as a crawler
- beautifulsoup4, requests - Retrieve and extract data sources from web
- pymongo - Upload and download retrieved resumes from MongoDB instance hosted on AWS
- nltk, gensim, scikit-learn - Peform data cleansing (stop words, stemming), create LDA topic model, create TF-IDF matrics, calculate LSI and cosine distance

---

## Process
  1. Crawl Indeed Resumes to retrieve a collection of resumes matching the select search terms (mechanical engineer, data scientist, data engineer, etc.)
  2. Upload each resume retrieved to MongoDB in AWS since data set is quite large (+10gb)
  3. Clean data set (remove stop words, punctuations, etc., apply stemming)
  4. Create LDA topic model from cleaned corpus of resumes
  5. Cluster corpus of resumes based on their topics
  6. Apply same pre-processing transformations to uploaded resume to be tailored to new target career field and gather topics
  7. Change current resumes topics that most closely match current field to similar (synonymous) topics found in intended target field
  8. Measure cosine similarity between modified resume and target field resumes using TF-IDF and LSI
  9. Continue to repeat changes to current resume wording in order to more closely match target field resumes in terms of cosine distance

---

## Results
- Original [presentation](static/resume_tailor.pdf) delivered on 08/19/2016
