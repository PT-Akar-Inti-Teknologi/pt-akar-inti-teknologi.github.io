---
layout: page
title: Continuous Integration
permalink: /standards/ci/
parent: Standards
has_children: false
---

# Continuous Integration
{: .no_toc }

We're using [Jenkins](https://jenkins.akarinti.tech/) for automated workflow (pipeline) and [SonarQube](https://sonar.akarinti.tech/) for code analysis.

Jenkins and Sonarqube each requires `Jenkinsfile` and `sonar-project.properties` to be included in your repository. These files are specific to the programming language and framework you use. Please see some examples below.

1. TOC
{:toc}

## Examples

<table>
    <thead>
        <tr>
            <th>Language</th>
            <th>Framework</th>
            <th>Build</th>
            <th>Test</th>
            <th>Code Coverage</th>
            <th>Coding Standard</th>
            <th>Example</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=4>Typescript</td>
            <td>✅ <strong>NestJS</strong></td>
            <td><code>npm</code>/<code>yarn</code></td>
            <td><code>jest</code></td>
            <td><code>lcov</code></td>
            <td><code>eslint</code></td>
            <td><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_nestjs">example_jenkins_nestjs</a><br/><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_nestjs2">example_jenkins_nestjs2</a><br/><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_nestjs3">example_jenkins_nestjs3</a></td>
        </tr>
        <tr>
            <td>React</td>
            <td><code>npm</code>/<code>yarn</code></td>
            <td><code>jest</code></td>
            <td><code>lcov</code></td>
            <td><code>eslint</code></td>
            <td></td>
        </tr>
        <tr>
            <td rowspan=2>✅ <strong>Angular</strong></td>
            <td><code>npm</code></td>
            <td><code>jasmine</code> & <code>karma</code></td>
            <td><code>lcov</code></td>
            <td></td>
            <td><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_angular">example_jenkins_angular</a></td>
        </tr>
        <tr>
            <td><code>yarn</code></td>
            <td><code>jasmine</code> & <code>karma</code></td>
            <td><code>lcov</code></td>
            <td><code>eslint</code></td>
            <td><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_angular2">example_jenkins_angular2</a></td>
        </tr>
        <tr>
            <td rowspan=2>Java</td>
            <td rowspan=2>✅ <strong>Spring Boot</strong></td>
            <td><code>maven</code></td>
            <td><code>junit</code></td>
            <td></td>
            <td></td>
            <td><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_spring_maven">example_jenkins_spring_maven</a><br/><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_spring_maven2">example_jenkins_spring_maven2</a></td>
        </tr>
        <tr>
            <td><code>maven</code></td>
            <td><code>junit</code></td>
            <td><code>jacoco</code></td>
            <td><code>checkstyle</code></td>
            <td><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_spring_maven3">example_jenkins_spring_maven3</a></td>
        </tr>
        <tr>
            <td>PHP</td>
            <td>✅ <strong>Laravel</strong></td>
            <td><code>composer</code></td>
            <td><code>phpunit</code></td>
            <td><code>clover</code></td>
            <td><code>phpcs</code></td>
            <td><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_laravel">example_jenkins_laravel</a><br/><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_laravel2">example_jenkins_laravel2</a><br/><a href="https://github.com/PT-Akar-Inti-Teknologi/example_jenkins_laravel3">example_jenkins_laravel3</a></td>
        </tr>
        <tr>
            <td>Kotlin</td>
            <td>Kotlin</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>Swift</td>
            <td>Swift</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>Dart</td>
            <td>Flutter</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td>Python</td>
            <td>Django</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
</table>

## Setup

1. Add `Jenkinsfile` and `sonar-project.properties` to the root of your repository.
2. Modify `sonar.projectKey` and `sonar.projectName` inside `sonar-project.properties` to match your repository name and descripton.

That's it. The next commit you push will be picked up by Jenkins.
