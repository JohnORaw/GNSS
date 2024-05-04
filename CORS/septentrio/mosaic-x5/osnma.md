# OSNMA

Read [here](https://gssc.esa.int/navipedia/index.php/Galileo\_Open\_Service\_Navigation\_Message\_Authentication) to understand what OSNMA is.

To use OSNMA with the M-X5, you need Merkle and Public keys.&#x20;

1. Register for an account [here](https://www.gsc-europa.eu/).
2. It took a day to get the response to confirm I had an account.
3. Go to this [page](https://www.gsc-europa.eu/support-to-developers/osnma-public-observation-test-phase) and register to the OSNMA Public Observation Test Phase.
4. It took 2 days to get a response!
5. You should now see the menu options under GSP Products.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## Merkle Tree

1. Download the XML file
2. Get the value from Treenode ,x\_ji>. There were 5 in my XML file, I used the last. The file below is from an example on the Septentrio site, its not real!

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## Public Key

1. You need a system with OpenSSL installed.
2. Download the public key .crt file
3. To create **key.pub**, use the command

```
openssl x509 -in OSNMA_PublicKey.crt -pubkey -noout -out key.pub
```

4. Extract the public key using an editor. The file below is from an example on the Septentrio site, its not real!

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

## Test

In GNSS->OSNMA->Advanced Settings, insert the Merkle Key and the Public Key.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

It takes a few minutes to synchronize, but once it does...

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
