<!-- markdownlint-disable  MD033 -->

# Using the IBM Z Accelerated for Snap ML Container Image

# Table of contents

- [Overview](#overview)
- [Downloading the IBM Z Accelerated for Snap ML container image](#container)
- [Container Image Contents](#contents)
- [Snap ML Usage](#snapml)
- [A Look into the Acceleration](#acceleration)
- [Security and Deployment Guidelines](#security-and-deployment-guidelines)
- [Using the Code Samples](#code-samples)
- [Frequently Asked Questions](#faq)
- [Technical Support](#contact)
- [Versioning Policy and Release Cadence](#versions)
- [Licenses](#licenses)

# Overview <a id="overview"></a>

[Snap ML](https://www.zurich.ibm.com/snapml/) is a library that provides
high-speed training and inference of popular machine learning models on modern
computing systems.

On IBM® z16™ and later (running Linux on IBM Z or IBM® z/OS® Container
Extensions (IBM zCX)), for certain models, Snap ML can leverage new inference
acceleration capabilities that transparently target the IBM Integrated
Accelerator for AI through the
[IBM z Deep Neural Network](https://github.com/IBM/zDNN) (zDNN) library. The IBM
zDNN library contains a set of primitives that support Deep Neural Networks.
These primitives transparently target the IBM Integrated Accelerator for AI on
IBM z16 and later. No changes to the original model are needed to take advantage
of the new inference acceleration capabilities.

_Note. When using IBM Z Accelerated for Snap ML on either an IBM z15® or an IBM
z14®, Snap ML will transparently target the CPU with no changes to the model._

# Downloading the IBM Z Accelerated for Snap ML container image <a id="container"></a>

Downloading the IBM Z Accelerated for Snap ML container image requires
credentials for the IBM Z and IBM® LinuxONE Container Registry,
[icr.io](https://icr.io).

Documentation on obtaining credentials to `icr.io` is located
[here](https://ibm.github.io/ibm-z-oss-hub/main/main.html).

---

Once credentials to `icr.io` are obtained and have been used to login to the
registry, you may pull (download) the IBM Z Accelerated for Snap ML container
image with the following code block:

```bash
# Replace X.Y.Z with the desired version to pull, or remove to fetch the latest.
docker pull icr.io/ibmz/ibmz-accelerated-for-snapml:X.Y.Z
```

In the `docker pull` command illustrated above, the version specified above is
`X.Y.Z`. This is based on the version available in the
[IBM Z and LinuxONE Container Registry](https://ibm.github.io/ibm-z-oss-hub/containers/ibmz-accelerated-for-snapml.html).

---

To remove the IBM Z Accelerated for Snap ML container image, please follow the
commands in the code block:

```bash
# Find the Image ID from the image listing
docker images

# Remove the image
docker rmi <IMAGE ID>
```

---

\*_Note. This documentation will refer to image/containerization commands in
terms of Docker. If you are utilizing Podman, please replace `docker` with
`podman` when using our example code snippets._

# Container Image Contents <a id="contents"></a>

To view a brief overview of the operating system version, software versions and
content installed in the container, as well as any release notes for each
released container image version, please visit the `releases` section of this
GitHub Repository, or you can click
[here](https://github.com/IBM/ibmz-accelerated-for-snapml/releases).

# Snap ML Usage <a id="snapml"></a>

For documentation on how to train and run inferences on models with Snap ML
please visit the official
[Snap ML documentation](https://snapml.readthedocs.io/en/latest/).

# A Look into the Acceleration <a id="acceleration"></a>

On IBM z16 and later, Snap ML provides accelerated inference for tree-ensemble
models via the IBM Integrated Accelerator for AI. These models can either be
trained using Snap ML, or trained using external software frameworks (such as
scikit-learn, XGBoost or LightGBM) and then imported into Snap ML. For more
information on exactly which models and frameworks are supported, please see the
[model import documentation](https://snapml.readthedocs.io/en/latest/model_import.html).

When importing models, if the `tree_format` parameter is set to `auto`, Snap ML
will automatically detect whether the IBM Integrated Accelerator for AI is
available. If it is available, Snap ML will optimize the model for execution on
the IBM Integrated Accelerator for AI. If not, Snap ML will optimize the model
for execution on the CPU.

# Security and Deployment Guidelines <a id="security-and-deployment-guidelines"></a>

- For security and deployment best practices, please visit the common AI Toolkit
  documentation found
  [here](https://github.com/IBM/ai-toolkit-for-z-and-linuxone).

# Using the Code Samples <a id="code-samples"></a>

Extensive code samples, in the form of Jupyter notebooks, can be found in our
[examples repository](https://github.com/IBM/snapml-examples). In particular, an
example of accelerated inference for a Random Forest model can be found
[here](https://github.com/IBM/snapml-examples/blob/main/examples/inference/random_forest/example_credit_card_fraud.ipynb).

# Frequently Asked Questions <a id="faq"></a>

## Q: Where can I get the IBM Z Accelerated for Snap ML container image?

Please visit this link
[here](https://ibm.github.io/ibm-z-oss-hub/containers/ibmz-accelerated-for-snapml.html).
Or read the section titled
[Downloading the IBM Z Accelerated for Snap ML container image](#container).

## Q: Where can I run the IBM Z Accelerated for Snap ML container image?

You may run the IBM Z Accelerated for Snap ML container image on IBM Linux on Z
or IBM® z/OS® Container Extensions (IBM zCX).

_Note. The IBM Z Accelerated for Snap ML will transparently target the IBM
Integrated Accelerator for AI on IBM z16 and later. However, if using the IBM Z
Accelerated for Snap ML on either an IBM z15 or an IBM z14, Snap ML will
transparently target the CPU with no changes to the model._

# Technical Support <a id="contact"></a>

Information regarding technical support can be found
[here](https://github.com/IBM/ai-toolkit-for-z-and-linuxone).

# Versions and Release cadence <a id="versions"></a>

IBM Z Accelerated for Snap ML will follow the semantic versioning guidelines
with a few deviations. Overall IBM Z Accelerated for Snap ML follows a
continuous release model with a cadence of 1-2 minor releases per year. In
general, bug fixes will be applied to the next minor release and not back ported
to prior major or minor releases. Major version changes are not frequent and may
include features supporting new IBM Z hardware.

## IBM Z Accelerated for for Snap ML versions

Each release version of IBM Z Accelerated for Snap ML has the form
MAJOR.MINOR.PATCH (X.Y.Z). For example, IBM Z Accelerated for Snap ML version
1.2.3 has MAJOR version 1, MINOR version 2, and PATCH version 3. Changes to each
number have the following meaning:

### MAJOR / VERSION

All releases with the same major version number will have API compatibility.
Major version numbers will remain stable. For instance, 1.Y.Z may last 1 year or
more. It will potentially have backwards incompatible changes. Code and data
that worked with a previous major release will not necessarily work with the new
release.

### MINOR / FEATURE

Minor releases will typically contain new backward compatible features,
improvements, and bug fixes.

### PATCH / MAINTENANCE

Maintenance releases will occur more frequently and depend on specific patches
introduced (e.g. bug fixes) and their urgency. In general, these releases are
designed to patch bugs.

## Release cadence

Feature releases for IBM Z Accelerated for Snap ML occur about every 6 months in
general. Hence, IBM Z Accelerated for Snap ML X.3.0 would generally be released
about 6 months after X.2.0. Maintenance releases happen as needed in between
feature releases. Major releases do not happen according to a fixed schedule.

# Licenses <a id="licenses"></a>

The International License Agreement for Non-Warranted Programs (ILAN) agreement
can be found
[here](https://www14.software.ibm.com/cgi-bin/weblap/lap.pl?li_formnum=L-AFCU-KDHVFK))

The registered trademark Linux® is used pursuant to a sublicense from the Linux
Foundation, the exclusive licensee of Linus Torvalds, owner of the mark on a
worldwide basis.

IBM, the IBM logo, and ibm.com, IBM z16, IBM z15, IBM z14 are trademarks or
registered trademarks of International Business Machines Corp., registered in
many jurisdictions worldwide. Other product and service names might be
trademarks of IBM or other companies. The current list of IBM trademarks can be
found [here](https://www.ibm.com/legal/copyright-trademark).

For additional disclaimers, please visit the general AI Toolkit documentation
found [here](https://github.com/IBM/ai-toolkit-for-z-and-linuxone).
