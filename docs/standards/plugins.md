---
layout: page
title: Plugins & Module
permalink: /standards/plugins-module/
parent: Standards
has_children: false
---

# Plugins & module
{: .no_toc }

### Tools
- [Github x Sonar Integration](https://github.com/PT-Akar-Inti-Teknologi/sonar_quality_gate_plugin)
  
  Tools to add sonar quality gate report in github pull request. Report will be sent as comment review, including any smell code, security issue, etc, when pull request is made. Need devops team to integrate it.

- [Github x Bitrix Integration](https://github.com/PT-Akar-Inti-Teknologi/ait_github_bitrix_plugin)

  Tools to add bitrix comment, integrated with github pull request. Comment will be sent to related Bitrix card when pull request is approved. Need to follow pull request template and need devops team to integrate it.

### Java Module
- [AIT Lumbung](https://github.com/PT-Akar-Inti-Teknologi/ait_lumbung_java_library)
  The library that used to upload and download file. This library supports: 
  - Local Storage
  - Google Cloud Storage
  - AWS S3
  - Alibaba OSS
  - Azure Blob Storage
  - Hitachi Cloud Platform Storage

### NodeJs Module
- [AIT NestJs Notification](https://github.com/PT-Akar-Inti-Teknologi/ait-nestjs-notification)
  Notification Module is a collection of modules or services that handle specific tasks and can be used in other modules or services that require such as sending email and sending SMS/OTP. This module supports:
  - Email: mailtrap, sendinblue, mailgun, sendgrid, and standard smtp protocol using node-mailer
  - SMS/OTP: Citcall, Fazpass, Twilio
  
- [AIT NestJs Storage](https://github.com/PT-Akar-Inti-Teknologi/ait_nestjs_s3_storage)
   The library that used to upload and download file. This library may not stable yet.