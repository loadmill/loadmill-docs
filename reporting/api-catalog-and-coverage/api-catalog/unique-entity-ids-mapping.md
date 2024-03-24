# Unique Entity ID's Mapping

Custom id patterns, such as prefixed/suffixed IDs may be not recognized automatically during the mapping stage. Use entity IDs mapping settings to prevent duplicate APIs, to streamline catalog organization and when you recognize static IDs in the api-catalog.

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption><p>Policy id wasn't automatically mapped as it is custom prefixed</p></figcaption></figure>

Here are the steps to map the ID:

1. Head to settings, in the dotted menu at the top-right corner of the screen\
   &#x20;![](<../../../.gitbook/assets/image (4) (1).png>)
2. Select 'PER-SERVICE' tab and insert a unique regular-expression into 'Ids Path Regexes'.

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>In our case, the id prefixed with 'cust' followed with four digits (<code>cust\d{4}</code>)</p></figcaption></figure>

3.  Select 'Apply changes to existing APIs' in order to re-map existing api's and click on save.\


    <figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>The result will show one unified endpoint with a placeholder for the id.</p></figcaption></figure>



Notes:

* Loadmill tracks changes in the API-catalog, a previous state can be achieved by selecting "Undo Settings Changes" in the top right corner dotted menu.\
  ![](<../../../.gitbook/assets/image (9).png>)
* The id is evaluated on individual part of the path in the url, the specified regex should match just the id part between/after the slash/es.
