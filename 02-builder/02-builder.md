### Builder <!-- element style="display:none" -->

![[builder.png | 400]](./imgs/builder.png)

Позволяет создавать сложные объекты пошагово.

::: block <!-- element style="display: none;" -->
```mermaid
flowchart LR
  A[X_Builder] -- "buildFeature_1()" --> B(X_Builder)
  B[X_Builder] -- "buildFeature_2()" --> C(X_Builder)
  C[X_Builder] -- "build()" --> E(Result object)
```
:::

--

#### Builder: example #1

```js
const request = new PaymentRequest()
  .setSenderName("John Doe")
  .setSenderCardNumber("0000 1111 2222 3333")
  .setSenderCardDate("01/26")
  .setSenderCardCvv("000")
  .setReceiverCardNumber("3333 2222 1111 0000")
  .setReceiverName("Jane Doe")
  .setAmount(100)
  .setApiKey("qwerty")
  .getRequest();

performTransaction(request);
```

--

#### Builder: example #1

```js
class PaymentRequest {
  constructor() {
    this.request = {
      sender: {},
      receiver: {},
      data: {}
    };
  }

  setSenderCardNumber(cardNumber) {
    this.request.sender.cardNumber = cardNumber;

    return this;
  }

  setSenderCardCvv(cvv) {
    this.request.sender.cvv = cvv;

    return this;
  }

  setSenderCardDate(date) {
    this.request.sender.expireDate = date;

    return this;
  }

  setSenderName(fullName) {
    this.request.sender.name = fullName;

    return this;
  }

  setReceiverCardNumber(cardNumber) {
    this.request.receiver.cardNumber = cardNumber;

    return this;
  }

  setReceiverName(fullName) {
    this.request.receiver.name = fullName;

    return this;
  }

  setApiKey(key) {
    this.request.data.key = key;

    return this;
  }

  setAmount(amount) {
    this.request.data.amount = amount;

    return this;
  }

  getRequest() {
    return this.request;
  }
}
```

back: [[📖 presentation#Builder]] <!-- element style="display:none" -->
