# Introduction to Helm

This POC provides an easy-to-understand introduction to [Helm](https://helm.sh) , an open-source package manager for Kubernetes. It explains the key concepts, goals, and features of Helm.

## What Is Helm?

__Helm__ is a tool that helps manage software built for Kubernetes. It acts as a package manager, allowing you to provide, share, and use applications, tools, and services within a Kubernetes cluster. The name "Helm" is a play on words combining the nautical nature of Kubernetes (meaning "ship's captain" in Greek) and the steering mechanism of a ship.

Helm was initially created in 2015 by Deis, which was later acquired by Microsoft. The Helm project evolved over time, merging with Google's Deployment Manager for Kubernetes, and it has become the main Helm project.

## Key Terms and Concepts

To understand Helm better, it's important to be familiar with these key terms and concepts:

- **Chart**: A Helm package that contains all the necessary resource definitions to run an application, tool, or service in a Kubernetes cluster.

- **Repository**: A place where charts can be collected and shared, similar to Perl's CPAN archive or the Fedora Package Database but for Kubernetes packages.

- **Release**: An instance of a chart running in a Kubernetes cluster. You can install a chart multiple times in the same cluster, and each installation creates a new release. For example, if you want two databases running in your cluster, you can install the MySQL chart twice, resulting in two releases, each with its own release name.

In summary, Helm installs charts into Kubernetes, creating a new release for each installation. You can find new charts by searching Helm chart repositories.

## Goals for Helm

The main goals of Helm are as follows:

- Make it easier to use Kubernetes.

- Provide a package manager similar to those found in operating systems.

- Emphasize security, reusability, and configurability for deploying applications to Kubernetes.

## Package Management Features

Helm offers the following package management features:

- Package repositories and search capabilities to discover available Kubernetes applications.

- Familiar commands for installation, upgrade, and deletion of packages.

- Configuration options to customize packages prior to installation.

- Tools to view installed packages and their configurations.

## Security Features

Helm includes security features to ensure the integrity and trustworthiness of packages:

- Cryptographic verification to ensure packages come from trusted sources.

- Secure network connections for package retrieval.

- Cryptographic verification to detect tampering of packages.

- Easy inspection of package contents to understand their functionality.

- Visibility into package configuration and the impact of different inputs on package output.

## Reusability Features

Helm supports the repeated and predictable installation of the same application in the same Kubernetes cluster or namespace. It provides patterns for storing configurations so that a combination of a chart and its configuration can be repeated easily. Helm was designed to be a package manager that can be shared across different Kubernetes distributions.

## Configurability Features

Helm offers tools to configure packages during installation and upgrades. While Helm is not primarily a configuration management tool, it supports basic lifecycle actions such as install, upgrade, and delete. Other tools like Helmfile, Flux, and Reckoner complement Helm by providing additional configuration management capabilities.

Kubernetes supports two main formats, JSON and YAML, for declaring the resources you want to deploy.