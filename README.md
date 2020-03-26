# NBAPI - API for NBdomain

NBdomain is [blockchain domain names](https://medium.com/@NBdomain/nbdomain-blockchain-domains-for-a-better-internet-bcd07213ef5c) and also can also be used as the user's [Global ID](https://medium.com/coinmonks/nbdomain-a-global-id-owned-by-you-26539e05245), an [Updatable Datastore](https://medium.com/@NBdomain/nbdomain-an-updatable-datastore-for-blockchain-37e84d9af16e) .

All domain information is saved on BSV blockchain, so anyone can resolve the domain independently. We have built a HTTP endpoint to make it as easy as possible.

## HTTP API

### EndPoint:
https://api.nbdomain.com/v1/?nid=%domain
where %domain can be main domain name like, 12345.test or subdomain name like, abc.12345.test .

### Return value

* When query for main domain

```
{
   "code":0,  // (int) Response code of the request.
   "message":"SUCCEED",  // (string) Response message.
   "obj":{
      "nid":"example.bsv",  // (string) A nbdomain.
      "owner_key":<Public key>,  // (string) Public key of the domain owner.
      "owner":<Address>,  // (string) Address of domain owner.
      "status":<Status>,  // (int) Status of the domain.
      "keys": {  // (Object) List of key, value pairs in domain space.
          subdomain1: value1,
          subdomain2: value2,
          ...
      },
      "admins":{  // (Object) List of key, value pairs of administrators.
		  alias1: <Administrator address>,
		  alias2: <Administrator address>,
		  ...
      },
      "tfdetail":{
          price: <Price>,  // (int) Listing price of a domain.
          buyer: <Address>,  // (string) Buyer address.
          expire: <Timetamp>,  // (int) Expired timestamp of a transfer command.
          seller: <Address>,  // (string) Seller address.
          tx: <tx>,  // (string) Hash of the transaction which will used to accept a domain transfer.
	  }
   }
}
```
* When query for subdomain

```
{
   "code":0,  // (int) Response code of the request.
   "message":"SUCCEED",  // (string) Response message.
   "obj": result //(string) value of the subdomain.
}

