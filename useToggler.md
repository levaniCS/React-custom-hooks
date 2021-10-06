## Provides a boolean state variable that can be toggled between its two states.







**[Example link](https://codepen.io/pen/?&prefill_data_id=297231c1-195a-457b-889d-24bf7c7cc63f)**



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