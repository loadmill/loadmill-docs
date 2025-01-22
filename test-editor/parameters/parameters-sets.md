# Parameters Sets

Inside the Parameters page, there is an option to insert a parameters set. This adds each parameter defined in the desired set to the current parameters list.&#x20;

### Creating a Parameters Set

The page is located under TEST DESIGN -> Parameters Sets.

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

Creation of a new set:

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FdpArucxnjFEpFj9tS0U4%2FParametersSet.mp4?alt=media&token=93d1df87-0a89-46d2-8078-2da7275d0c00" %}

A set that hasn't been published even once will be saved as a 'draft':

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

Changed but unpublished sets will be saved as 'modified' (<img src="../../.gitbook/assets/image (6) (1).png" alt="" data-size="original">).

### Importing/Exporting Parameters Sets

A Parameters Set can also be represented in a YAML file with the following structure:

```yaml
meta:
  description: Example Parameters Set
parameters:
  - name1: "Foo"
  - name2: "Bar"
```

An example use case is to duplicate a set and modify it (![](<../../.gitbook/assets/image (8) (1).png>), ![](<../../.gitbook/assets/image (9) (1).png>)).

### Exporting as a key-value file

From inside the parameters sets editor, it is possible to download only the parameters as a key-value .txt file, e.g.:&#x20;

```
name1=Foo
name2=Bar
```

It is good for Loadmill's CI integration, where inline parameters can be overridden or added by providing a key-value file instead (See "Parameters" in [Loadmill's NPM README](https://www.npmjs.com/package/loadmill?activeTab=readme)).

<figure><img src="../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

