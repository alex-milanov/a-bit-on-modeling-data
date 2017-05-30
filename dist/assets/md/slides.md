# a Bit on Modeling Data

## ... that plays well across multiple devices and user experiences

### ... or yet another way I've thought of how to promote my framework

### ... which is pretty RAD btw.

### ... and these slides are actually running on top of it

### ... and now it's running on top
```js
// actions
const actions$ = new Rx.Subject();
const actions = {
	incr: () => actions$.onNext(
		state => ({num: state.num + 1})),
	initial: {num: 0}
};

// ui
const {div, span, button} = vdom;
const ui = ({state, actions}) => div('#ui', [
	button({on:{click: () => actions.incr()}}, 'Incr'),
	span(`Num: ${state.num}`)
]);

// reducing the stream of actions to the app state
const state$ = actions$
	.startWith(() => actions.initial)
	.scan((state, reducer) => reducer(state), {})
	.share();

// mapping the state to the ui
const ui$ = state$.map(state => ui({state, actions}));

vdom.patchStream(ui$, document.querySelector('#ui'));
```

## Motivation

### Technical Debt
![technical-debt](./assets/img/technical-debt.png)

### Reflection
![reflection](./assets/img/tree.png)

### Connect some dots
![connecting-dots](./assets/img/connecting-dots.jpg)

### Pandora's box
![pandora](./assets/img/pandora.jpg)

## Meta Concepts

### The Map is not the Territory

### Iteration

### Thesis -> Antithesis -> Synthesis

### Jeet Kune Do

## Domain Driven Design
![ddd-diagram-example](./assets/img/ddd-diagram-example.png)

### DDD: Ubiquitous Language

### DDD: Bounded Context

### DDD: Building Blocks
- Aggregates
- Entities
- Value Objects
- Services

### Event Sourcing
![event-sourcing](./assets/img/event-sourcing.png)

### CQRS or CQS
![cqrs](./assets/img/cqrs.png)

### React, Redux, Flow
![react-redux-flow](./assets/img/react-redux-flow.jpg)

### App Architecture
![app-architecture](./assets/img/app-architecture.png)

### More Info
- https://tiny.cc/iblokz-dev-guide
- https://github.io/iblokz/ui-boilerplate
- https://github.com/alex-milanov/simple-tasks-example

## Further Read
- https://martinfowler.com - Martin Fowler's guide to everything
- https://www.mongodb.com/blog/post/event-sourcing-with-mongodb - Good description of Event Sourcing and CQRS
- https://staltz.com/nothing-new-in-react-and-flux-except-one-thing.html
- https://github.com/reactjs/redux/issues/351 - Redux and it's relation to CQRS (and other things)
- https://medium.com/javascript-scene/10-tips-for-better-redux-architecture-69250425af44

### Ontology and Taxonomy

### Neurological Levels
![logical-levels](./assets/img/logical-levels.png)

### UML vs Diagrams


## Examples


## Questions
