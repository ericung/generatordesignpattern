# generator design pattern

Start with state version and state generator variables

Functions for generating for each generator variable

A Generate button

Render Function based on state version

Main function to operate on

```javascript
function FibonacciState() {
    const [stateX, setStateX] = useState('a');
    const [stateY, setStateY] = useState('b');
    const [stateZ, setStateZ] = useState('');
    const [state, setState] = useState('Z');

    function stateXGenerator() {
        setStateX(stateY + stateZ);
        setState('Y');
    }

    function stateYGenerator() {
        setStateY(stateZ + stateX);
        setState('Z');
    }

    function stateZGenerator() {
        setStateZ(stateX + stateY);
        setState('X');
    }

    function Generate() {
        switch (state) {
            case 'X': stateXGenerator(); break;
            case 'Y': stateYGenerator(); break;
            case 'Z': stateZGenerator(); break;
        }
    }

    function Render() {
        switch (state) {
            case 'X': return (<textarea value={stateX}></textarea>)
            case 'Y': return (<textarea value={stateY}></textarea>)
            case 'Z': return (<textarea value={stateZ}></textarea>)
        }
    }

    return (
        <div>
            <button type="submit" onClick={Generate}>
                Generate
            </button>
            {
                Render()
            }
        </div>
    );
}

```
