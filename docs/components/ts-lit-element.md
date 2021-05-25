---
layout: page
title: TypeScript and Lit [TODO]
permalink: /components/ts-lit-element/
parent: Third party integration
nav_order: 5
---

# Build your own component with Vaadin Flow (Vaadin 14.5+)

The Vaadin 14.5 *minor* update backported Typescript configuration: You don't need to do anything in your application to use Typescript instead of Javascript.
That's my favorite way to build custom component.

This chapter explains how to build a custom component and explain different ways to communicate between the backend and the frontend.
It's specific to Flow and does not work for Fusion.

## Create a Typescript component
```ts
import {css, customElement, html, LitElement, property} from 'lit-element';

@customElement('my-test-component')
export class MyTestComponent extends LitElement {

    static get styles() {
        return css`
        :host {
            display: block;
        }
        `;
    }

    private $server?: MyTestComponentServerInterface;

    @property({ attribute: true })
    private test: String = "test";

    private clickAction() {
        this.$server!.displayNotification("Click on button");
    }

    private titleClickedEvent() {
        this.dispatchEvent(new CustomEvent('title-clicked', {
            // you can add detail: {kicked: true},
            cancelable: true
        }));
    }

    public replaceTestVariable(newValue: string) {
        this.test = newValue;
    }
    /**
     * Main method of the component
     *
     */
    render() {
        return html`<div>Test attribute ${this.test}</div>
        <div @click=${this.titleClickedEvent}>Title</div>
                    <div><button @click=${this.clickAction}>Call Notification</button></div>
        `;
    }

}

interface MyTestComponentServerInterface {
    displayNotification(text: string): void;
}

```

## Create a Java component
```java
@JsModule("./my-test-component.ts")
@Tag("my-test-component")
public class MyTestComponent extends Component {

    public MyTestComponent() {
    }

    public String getTest() {
        return getElement().getProperty("test");
    }

    public void setTest(String test) {
        getElement().setProperty("test", test);
    }

    @ClientCallable
    private void displayNotification(String text) {
        Notification.show("Notification: " + text);
    }

    public void replaceTestVariable(String newValue){
        getElement().callJsFunction("replaceTestVariable", newValue);
    }

    public Registration addTitleClickListener(ComponentEventListener<MyTestComponentClickEvent> listener) {
        return addListener(MyTestComponentClickEvent.class, listener);
    }

    @DomEvent("title-clicked")
    public static class MyTestComponentClickEvent extends ComponentEvent<MyTestComponent> {

        public MyTestComponentClickEvent(MyTestComponent source, boolean fromClient) {
            super(source, fromClient);

        }
    }
}
```

## How the link between both is done?

`@JsModule` is loading the file and add the content in the Vaadin bundle but doesn't load the component.
Inside the web component, you define a new custom element in the browser CustomElementRegistry with `@customElement('my-test-component')`. (The annotation is Typescript specific)

The `@Tag` will load the component defined in the CustomElementRegistry. 

Warning
{: .label .label-red }
Always name your tag with a dash `-` inside, you can't name it mytestcomponent it won't be accepted by the browser.

## How to send data to the frontend?

###  Attributes

On the client side you can add attributes or properties that are listened 

###  Execute Javascript or call javascript function


## How to send data to the backend?

###  $server and ClientCallable

When the component is bound to the backend, Flow instantiates a variable $server. It helps to call all the Java methods `@ClientCallable` from the frontend.

With TypeScript 


###  Event

You can send an event on the 