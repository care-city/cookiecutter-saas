{{ cookiecutter.project_slug }}
===============================
A short description of the project.

[![Cookiecutter-webpack](https://img.shields.io/badge/built%20with-Cookiecutter%20Webpack-f38230.svg)][cookiecutter-webpack]


Getting Started
---------------

Install npm packages

    $ npm install

Start the server

    $ npm start


Open up http://localhost:8080 in your browser.


Basic Usage
-----------

### Running tests
This project uses [`karma`][karma] for running tests with [`mocha`][mocha] for the test framework and @mjackson's [`expect`][expect] library for assertions and test doubles.

    $ npm test

This will run all tests in the [`./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/__tests__`][test-dir] directory.

### Coverage

A coverage report will be generated by running the `$ npm test` command and outputted into the build directory.

Open the lcov-report for an overview of your code coverage:

    $ open {{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/dist//reports/coverage/lcov-report/index.html


---------------------------------


React-Redux Project Structure
-----------------------------
Outline the structure of the project.

#### Source `./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/`
Main project source.

#### Actions `./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/actions/`
Action creators. These are triggered by events and return an action object that will notify reducers that a change needs to be reflected in the state.

#### Components `./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/components/`
React components. Mostly __dumb__ components.

#### Constants `./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/constants/`
Stuff that doesn't change. Redux action types.

#### Containers `./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/containers/`
React components that serve as containers for multiple _dumb_ components. These should connect React components to a Redux store using the [react-redux connect method](https://github.com/reactjs/react-redux/blob/253ce8b3068d9d9bfe55f70a6f18a5fde313b326/docs/api.md#connectmapstatetoprops-mapdispatchtoprops-mergeprops-options).

The _connect_ method will __map state to props__ by subscribing to a __store__ that has been passed though the components __context__ and will tell the component to update whenever the state changes.

_Connect_ can also __map dispatch to props__ by connecting _action creators_ to and to the _store dispatch_ method allowing the _props_ to be invoked directly (rather than `store.dispatch({type: 'MY_ACTION', id: 1, other_stuff: 'blah'})`).

#### Reducers `./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/reducers/`
Reducer functions that take in the _current state_ and an _action type_ then return a new state.

#### Store `./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/store/`
Custom store for adding middleware.


---------------------------------


Configuration
-------------

### Settings
There are two setting configurations: _Local_ and _Production_. Both of these settings inherit from the _Base_ settings. The main _Router_ will determine which setting is being requested based on the `NODE_ENV`: `[production, local, test]`.

#### Router `./webpack.config.js`
* Routes to other webpack configs
* Passes main options to other configs

#### Base `./config/webpack.base.config.js`
* Provide entry endpoints
* Output endpoints
* Common plugins

#### Local `./config/webpack.local.config.js`
* Point to the local publicPath
* Local plugins

#### Production `./config/webpack.production.config.js`
* Point to the production publicPath
* Minimize code
* Production plugins

### Templates
[Template options](https://github.com/jaketrent/html-webpack-template/blob/faac42d0720d52b444e65aa9a151e0ad8504effc/README.md#basic-usage)
-----------------------------------

Redux Dev Tools
---------------
Redux dev tools allows you to debug redux. See the [redux-devtools github repository](https://github.com/gaearon/redux-devtools) for more info.

You can add more [monitors](https://github.com/gaearon/redux-devtools/blob/a21905cbdeb22fc67c3f16caa8752cb5b4133b32/README.md#custom-monitors) by installing the monitors package and adding the component inside the `DockMonitor` component found in [`./{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/containers/DevTools.js`](containers/DevTools.js).

### Controls
The controls can be configured by editing the `DockMonitor` component's attributes. Currently the controls are:

    toggleVisibilityKey="ctrl-h"
    changePositionKey="ctrl-q"
    changeMonitorKey="ctrl-m"


<!-- references -->
[karma]: https://github.com/karma-runner/karma
[mocha]: https://github.com/mochajs/mocha
[expect]: https://github.com/mjackson/expect
[cookiecutter-webpack]: https://github.com/hzdg/cookiecutter-webpack

[test-dir]: /{{ cookiecutter.project_slug }}/static/{{ cookiecutter.project_slug }}/__tests__/
