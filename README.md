# IxO 

### Thinking and programming interaction
*What:* IoX is a framework for helping interaction design students think and programming interaction. It brings together a conceptualisation of interaction with a structured programming model for how to code and design interactive experiments and prototypes in educational contexs. 

*Background:* How this is comes out of teaching students interactivity.  

*Motivation (why):*
Existing alternatives and what they are lacking: 
* What is already outhere: 
* The need for a *structured* approach to programming interactivity rather than a general approach to programming. Interaction design students are not expected to be expert programmers, but should be able to
* Existing frameworks for creative coding like p5.js are fine, but lack a focus specifically on programming interaction.
* Existing UI frameworks like React, Svelte, Angular are to  geared towards designing graphical user interfaces, which is often to specific a use case for more a more open and experimental approach to interaction design.
* Prototyping tools like Figma, that don't require programming skills, are similarly geared towards GUIs. 
* Existing approaches are also typically not made to experiment with new approaches to interaction, but do rather rely on and implement conventional ones.
* Finally, existing approaches are not grounded in an explicitly conception of interaction, but might rely implicitly on conventional ones. Interaction designers need a proper language for talking about interaction in creating and evaluating interaction designs. 

*How:* How is this document weighted structured? An introduction to 'thinking interaction' and then a more elaborated descriptions and examples of how 

*Prerequisits:* Bringing together a conceptualisation of interaction with a framework for programming for interaction
 

*What it is not:* Not meant to build 

## Conceptualising interaction and programming interaction designing a (technical) object and the challenges of connecting the two

### Tool, object, atmosphere, agent
From the experiential perspective it is even problematic to talk about 'interaction' -- often what we are designing is 'action' 

## Conceptualisation and programming architecture
When thinking about how to program interaction we can think certain conceptualisations and programming architecture. In essence, programming interaction is about receiving an input and generating an output. The generated output is usually dependent on the input. When input and output are continuous an interactional arc is established. Another way of saying it is that the output is a function of the input.

## Programming interaction: IxO

### A simple transformation of input to output 
Output as a function of input (I → O)

### More than one input
Output as a function of multiple input (I<sub>0</sub>, I<sub>1</sub>, I<sub>2..n</sub> → O)

### A sense of time: Past and present input to output
(I, I<sub>past</sub> → O)

### Introducing inner state: Output as a function of input and static state (I, S → O)

### State as function of input and output as a function state (I → S & S → O)

### Output as a function of input and self-generating state




 
## What is input?
What sorts of input should our system be able to receive (how should it be receptive)? This might both a hardware and software question. We might need certain hardware to be a able to receive certain input, but it is also often the case that we need to set up programmatically what input to listen to. 

### Separating between data and commands/requests
 Input can be data, e.g, a set of coordinates or something being pressed. When input are data it lends itself nicely to the idea of a continuous stream of data. But what about clicking a button '+' which signals a command rather than data. Sometimes a command can also have data, a payload, as in an input field. How do we deal with the concepts of a command and data as input. Conceptually, they seem quite different. The former is linguistic and discrete, where as the former is tracking bodily movement and continuous. An interesting example would be if we were to implement dragging behaviour. There is a dragging gesture which is first click/press and then move the pointer. We could easily have a stream recognising this gesture (derived input, see below) and we would also be able to collect the x and y of the pointer moving, even collect the whole dragging trajectory if we wanted or just the starting point and so on. However, the dragging gesture does not mean that something is actually being dragged. An object has to be 'below' the cursor if any dragging is going to happen and whatever object is being dragged might have to stay within some boundaries for example. In effect, that means that there is a decision to whether the drag gesture should actually result in an object being dragged. Thus, there is a dragging logic that needs to be implemented somewhere which decides whether a *request* to drag should be fulfilled or not. As soon as we have state and the possibility of illegal states that neccesitates the validation of input we are no longer conceptually talking about commands or even worse actions, but rather *action requests* and that might be given or not. 

 So we can set up a stream that is able to recognise a gesture (a combination of pointer gestures (press, move, lift --> startdragging, dragging, stopdragging) or even better and more true to what is going on (press, move, lift --> hold, pull, release) because we can pull without it anything being dragged). And the stream can then call a 'request handler' with the request, which then can respond to the request as it sees fit (accept, reject, or even have the object return to its original position when released traversing backwards the same trajectory it was pulled)

 So when is it that we need to introduce 'requests' as part of the architecture? That is basically when our input can result in our State being in an illegale state that needs to be checked for, that is, cannot just make the State a function of the input willy-nilly. 

*Combining multible sources of input:* Input doesn't have to be singular, but can be combined from multiple sources of input. For example, we might combine input from a remote device with input from a local device.  

*Derived input:* We might derive secondary input from primary input. For example, we might be interested in the speed of mouse movement deriving it from inputs about change of mouse position. Or we might want an aggregate of input or remove noise from input and so on. Or a sequence of inputs in a particular order, e.g. mousedown+mousemove = drag.

We design the system to be receptive to certain inputs. This might simply be creating a button in an UI that can be clicked or more advanced an AI that can recognise body movement. Part of designing an interactive system is setting up a receptive 'surface' (in typical GUI terms, the view) through which the system can receive input.  

## What is output?

## What is a stream?
A stream are data flowing over time 

## What is state?
State can be transient and local to a particular or enduring and global across. If we have enduring state the storage and potentially validation of   

```javascript
/* 

two ways of defining a stream, one verbose using ixd conceptualisation, the other more terse. It serves as a template for how to organise and conceptualise a simple interactive arc as a program: Define an input source, define a pipeline that transforms the input and define an output where the result will be rendered in some form. 

input -> pipeline -> output 

*/



const input = from(delayedSequence())
const pipeline = pipe(
        setState(newState, initialState),
        map(data => data[0]),
        queue(5)
)
const output = (data) => console.log(data) 
pipeline(input).subscribe(output)

from(delayedSequence())
.pipe(
    setState(newState, initialState),
    map(data => data[1]),
    queue(5))
.subscribe((data) => console.log(data))

```

The output as a function of the input can, however, be done in different ways

*Direct* input -> output

*Mediated* input -> transformation -> output

## The role of state
### Transient state
### Shared state

## Transforming input

## The various roles of time 

## Output as a direct function of the input o(i)

## Output as function of input over time (transient state)

### Output as  as a function of input 


