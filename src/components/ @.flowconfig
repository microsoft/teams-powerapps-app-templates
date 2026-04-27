import React, { Component } from 'react';

class App extends Component {
  handleClick = () => {
    import('./moduleA')
      .then(({ moduleA }) => {
        // Use moduleA
      })
      .catch(err => {
        // Handle failure
      });
  };

  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Load</button>
      </div>
    );
  }
}

export default App;
  [options]
+ module.name_mapper='^\([^\.].*\)$' -> '<PROJECT_ROOT>/src/\1'  
[options] + module.name_mapper='^\([^\.].*\)$' -> '<PROJECT_ROOT>/src/\1'