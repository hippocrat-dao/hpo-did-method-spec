# HPO DID Method Specification

Hippocrat is a self-sovereign data protocol using bitcoin and peer-to-peer technology.

## 1. HPO DID Method Specific Identifier
HPO DID Method Specific Identifier format is following below:
```
hpo-did = "did:hpo:" + hpo-did-specific-idstring
hpo-did-specific-idstring = the first public key hex of HPO DID, same format as bitcoin public key
```

HPO DID Example:
```
did:hpo:030807a2c73c62760df3431f7cdeecf0fe898a7da61a7c598c17e372f93cb402e6
```

## 2. DID Document

### 2.1. HPO DID Document Example
HPO DID Document Example:
```json
{
    "@context": "https://www.w3.org/ns/did/v1",
    "id": "did:hpo:030807a2c73c62760df3431f7cdeecf0fe898a7da61a7c598c17e372f93cb402e6",
    "verificationMethod": [
        {
            "id": "did:hpo:030807a2c73c62760df3431f7cdeecf0fe898a7da61a7c598c17e372f93cb402e6",
            "type": "EcdsaSecp256k1VerificationKey2019",
            "controller": "did:hpo:030807a2c73c62760df3431f7cdeecf0fe898a7da61a7c598c17e372f93cb402e6",
            "publicKeyHex": "030807a2c73c62760df3431f7cdeecf0fe898a7da61a7c598c17e372f93cb402e6"
        }
    ]
}
```

## 2.2. CRUD

#### Create
* Creation of HPO DID document is supported in [hippocrat-wallet-sdk](https://github.com/hippocrat-protocol/hippocrat-wallet-sdk).
* HPO DID(or the data that can derive HPO DID) should be stored in user local storage.

#### Read
* User will fully owns DID in his or her own storage to achieve self-sovereignty.
* Basically, HPO DID is readable only when user allows on a client side.
* Additionally, the issuer can use peer-to-peer storage to provide the status of HPO DID.

#### Update
* Update is not supported for HPO DID document.

#### Delete (Revoke)
* Revoke by self can be simply done if user deletes in local.
* If the issuer stores the status of user's DID in public space(e.g. peer-to-peer storage), user can request to delete from that space.
* Resolver will use either user's local storage or peer-to-peer storage to search.


## 3. Security Considerations
* DID Document and Identifier are created following bitcoin spec(bip32, bip44 and so on) using [hippocrat-wallet-sdk](https://github.com/hippocrat-protocol/hippocrat-wallet-sdk). 
* Security level is same with bitcoin.

## 4. Privacy Considerations
* Privacy data can be stored in peer-to-peer storage and must be encrypted by user's public key using [hippocrat-wallet-sdk](https://github.com/hippocrat-protocol/hippocrat-wallet-sdk).
* DID document itself does not include any privacy information.

## References
[1]. https://github.com/bitcoin/bips

[2]. https://w3c.github.io/did-core
