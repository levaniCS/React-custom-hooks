## Provides a boolean state variable that can be toggled between its two states.







**[Example link](https://codepen.io/levanics/pen/QWgedxo)**



```javascript

const useToggler = initialState => {
  const [value, setValue] = React.useState(initialState);

  const toggleValue = React.useCallback(() => setValue(prev => !prev), []);

  return [value, toggleValue];
};
const Switch = () => {
  const [val, toggleVal] = useToggler(false);
  return <button onClick={toggleVal}>{val ? 'ON' : 'OFF'}</button>;
};
ReactDOM.render(<Switch />, document.getElementById('root'));

```