## This hook returns view port width and height


```javascript

const getWindowDimensions = () => {
  const { innerWidth: width, innerHeight: height } = window
  return {
    width,
    height,
  }
}

export default function useWindowDimensions() {
  const [windowDimensions, setWindowDimensions] = useState(getWindowDimensions())

  useEffect(() => {
    function handleResize() {
      setWindowDimensions(getWindowDimensions())
    }

    window.addEventListener('resize', handleResize)
    return () => window.removeEventListener('resize', handleResize)
  }, [])

  return windowDimensions
}


// Examples
const ResponsiveComponent = props => {
    const { width, height } = useWindowDimensions()

  return (
    <div>
        Viewport width: ${width} <br/>
        Viewport height: ${width} <br/>
    </div>
  );
};

ReactDOM.render(<ResponsiveComponent />, document.getElementById('root'));
```