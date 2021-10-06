## Handles the event of clicking outside of the wrapped component.

**[Example link](https://codepen.io/pen/?&prefill_data_id=8511633c-0f82-477e-a901-6968642e36ca)**

```javascript

const useClickOutside = (ref, callback) => {
  const handleClick = e => {
    if (ref.current && !ref.current.contains(e.target)) {
      callback();
    }
  };
  React.useEffect(() => {
    document.addEventListener('click', handleClick);
    return () => {
      document.removeEventListener('click', handleClick);
    };
  });
};


--
const ClickBox = ({ onClickOutside }) => {
  const clickRef = React.useRef();
  useClickOutside(clickRef, onClickOutside);
  return (
    <div
      className="click-box"
      ref={clickRef}
      style={{
        border: '2px dashed orangered',
        height: 200,
        width: 400,
        display: 'flex',
        justifyContent: 'center',
        alignItems: 'center'
      }}
    >
      <p>Click out of this element</p>
    </div>
  );
};

ReactDOM.render(
  <ClickBox onClickOutside={() => alert('click outside')} />,
  document.getElementById('root')
);
```