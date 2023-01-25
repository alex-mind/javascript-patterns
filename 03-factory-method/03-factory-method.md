### Factory Method <!-- element style="display:none" -->

![[factory-method.png | 400]](./imgs/factory-method.png)

Определяет общий интерфейс для создания объектов в суперклассе, позволяя подклассам изменять тип создаваемых объектов.

--

#### Factory method: example #1

```js
class Creator {
  factoryMethod() {/* abastruct */}

  someOperation() {
    const product = this.factoryMethod();

    return `Creator: Run ${product.operation()}`;
  }
}

class ConcreteProduct1 {
  operation() {
    return '{Result of the ConcreteProduct1}';
  }
}

class ConcreteProduct2 {
  operation() {
    return '{Result of the ConcreteProduct2}';
  }
}

class ConcreteCreator1 extends Creator {
  factoryMethod() {
    return new ConcreteProduct1();
  }
}

class ConcreteCreator2 extends Creator {
  factoryMethod() {
    return new ConcreteProduct2();
  }
}
```
--

#### Factory method: example #2

```js [|7-11|13]
class SuccessNotification {}
class ErrorNotification {}
class InfoNotification {}

class Component {
  factoryMethod (type = '') {
    const notificationTypes = {
      succes: SuccessNotification,
      error: ErrorNotification,
      info: InfoNotification
    };

    const notification = new notificationTypes[type];

    return notification;
  }
}
```

back: [[📖 presentation#Factory Method]] <!-- element style="display:none" -->
