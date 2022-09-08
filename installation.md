---
description: Quick overview of system requirements and installation instructions
---

# 🧠 Installation

CNext is currently available as a local install (with a SaaS version to follow shortly).&#x20;

Two installation options are available to users:

* pip install
* Docker

## PIP Installation

{% hint style="danger" %}
_PLEASE NOTE: CNext requires **npm >= 18.4** and **Python >= 3.9.7**_ . _Please ensure your environment meets the minimum requirements before beginning the installation._&#x20;
{% endhint %}

#### **Step 1: Install**&#x20;

Run command:

```python
pip install -U cnext
```

#### Step 2: CNext Initialization

Run command:

```
cnext
```

You'll be prompted to download our sample project (this project has sample code, datasets and some basic tutorials you can play around with to familiarize yourself with the system) - I'd recommend selecting 'Y'

Save the sample project to your desired location (please use an absolute path) - e.g. _/Users/luke/Downloads/cnext/Skywalker._&#x20;

On subsequent runs you can skip the sample project download.

#### Step 3: bring up the system in your browser

If everything completed without any errors open your browser and navigate to:

```
http://localhost:4000
```

By default the portal will come up on port 4000.&#x20;

## Docker Installation

#### Step 1: Run the following command

\*For MacOS Monterey users you may have a port conflict on port 5000, please take a look at the following to[ turn off your AirPlay receiver. ](https://medium.com/pythonistas/port-5000-already-in-use-macos-monterey-issue-d86b02edd36c)

```python
docker run --rm -it -p 4000:4000 -p 5000:5000 -p 5011:5011 -p 5008:5008 -p 5005:5005 cycai/cnext
```

If everything completed without any errors open your browser and navigate to:

```
http://localhost:4000
```

Note: to add a local directory for access within CNext you'll need to map the local drive to the home folder when provisioning the instance (add the -v parameter to the string above). Example below:

```
-v $(pwd)/Skywalker2:/home/cnext/Skywalker2
```

By default the portal will come up on port 4000.&#x20;
