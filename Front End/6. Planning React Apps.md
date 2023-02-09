# Planning React Apps

## Prior Knowledge

- Be able to create React components.
- Be able to create and update state using `useState`.
- Understand the flow of props in a React app.

## Learning Objectives

- Be able to break a React App into components from a wire-frame.
- Be able to plan what data will need to be held in state.
- Understand how to decided which components to hold state in.

## Creating new react apps

When creating a new React app there are a lot of potential configuration options to get things up and running. To make things easier the React team developed [create-react-app](https://create-react-app.dev/)

This is a tool that will allow us to setup new React applications with the default recommended settings and configure tools such as Babel and webpack to cut down the amount of boilerplate code we have to write.

New apps can be made using

```bash
npx create-react-app my-app-name
```

This will:

1. Create a new folder named `my-app-name`
2. Initialise a new project and install required dependencies
3. Create a new git repo and an initial commit if one does not exist
4. Setup an example app to get started with

**nb** There are some restrictions around the names you can give your apps, such as no capital letters (directories are case sensitive on linux but not on MacOS or Windows so always using lowercase is a good idea.) The cli will prompt you if you break the restrictions.

Once this app is setup you can remove any of the files you don't need and start creating your own app.

## Package managers

An alternative package manager to `npm` is [yarn](https://yarnpkg.com/). They both work from `package.json` files and if you have both `yarn` will be used by default. If you want to go back to using `npm` pass the `--use-npm` flag when creating your app.

```bash
npx create-react-app my-app-name --use-npm
```

If you don't have `yarn` installed then you can use the command normally.

## Wireframing and Components

When planning an app the first steps are to do some basic design work. In a professional environment this will often be handled by dedicated designers and for our purposes we will use some basic wireframing. Wireframes are a schematic, or blueprint, of the structure of a website. They do not need to come up with every aspect of the style or visual design and are focused around the functionality and general structure of our app.

These can be created using a number of tools or good old fashioned pen and paper. A quick sketch is enough for now but if you'd like to try them out some popular free tools are:

- [Excalidraw](https://excalidraw.com/)
- [Figma](https://www.figma.com/)
- [Miro](https://miro.com/)

Once you are happy with the structure of you App separate out the functionality into React components. You can have as many or as few components as you would like and the decision about what to group together is up to you. Things to consider when deciding on your components are:

- Abstraction - Grouping related functionality together. Websites tend to be made up of sections which make for ideal components. Things like `header`, `footer`, `nav` and `section` tags typically make for good components as all of the logic to do with that section can be grouped together.

- Re-useability - Components are re-useable. If you need some functionality repeating then abstracting the logic into it's own component allows you to re-use that component in several places.

- Complexity - Adding more components makes your component tree more complex. Is the functionality you are extracting complicated enough to warrant adding another component. If it's simple enough to just render in the parent you may not gain any value from extracting it to it's own component.

Once you have decided on your components sketching out a `component tree` is often helpful to visualise the parent-child relationship.

## Planning State

Once your component tree is established decide on what information your app will need to hold in state. Keep this state to a minimal, single source of truth. The structure of the state is up to you, as long as you can track all the information which will vary over time.

For each state variable make a list of which components will need access to that state in order to either read or update that state. This state needs to be declared in one of your components. That component must be high enough on the component tree so that every component that needs access is beneath it. This way the state and functions to update it can be passed down on props.

A good rule of thumb to follow here is to `place your state as low as possible, but as high as necessary`.

Repeat this process until all of your state has been placed on your component tree. This should give you a nice structure to work from with the important decisions about state and components being made before you jump into the code.

Don't worry if you make a mistake and place state to low on the component tree. You can always [lift state up](https://reactjs.org/docs/lifting-state-up.html) and move it to a higher component later on.
