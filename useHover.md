## Handles the event of hovering over the wrapped component.






**[Example link](https://codepen.io/pen/?&prefill_data_id=c144d1b6-b90d-4038-a9a9-67e7bd62582d)**



```javascript
const useHover = () => {
  const [isHovering, setIsHovering] = React.useState(false);

  const handleMouseOver = React.useCallback(() => setIsHovering(true), []);
  const handleMouseOut = React.useCallback(() => setIsHovering(false), []);

  const nodeRef = React.useRef();

  const callbackRef = React.useCallback(
    node => {
      if (nodeRef.current) {
        nodeRef.current.removeEventListener('mouseover', handleMouseOver);
        nodeRef.current.removeEventListener('mouseout', handleMouseOut);
      }

      nodeRef.current = node;

      if (nodeRef.current) {
        nodeRef.current.addEventListener('mouseover', handleMouseOver);
        nodeRef.current.addEventListener('mouseout', handleMouseOut);
      }
    },
    [handleMouseOver, handleMouseOut]
  );

  return [callbackRef, isHovering];
};
const MyApp = () => {
  const [hoverRef, isHovering] = useHover();

  return <div ref={hoverRef}>{isHovering ? 'Hovering' : 'Not hovering'}</div>;
};

ReactDOM.render(<MyApp />, document.getElementById('root'));

```