# `.getWrappingComponent() => ShallowWrapper`

If a `wrappingComponent` was passed in `options`, this methods returns a `ShallowWrapper` around the rendered `wrappingComponent`. This `ShallowWrapper` can be used to update the `wrappingComponent`'s props, state, etc.


#### Returns

`ShallowWrapper`: A `ShallowWrapper` around the rendered `wrappingComponent`



#### Examples

```jsx
import { Provider } from 'react-redux';
import { Router } from 'react-router';
import store from './my/app/store';
import mockStore from './my/app/mockStore';

function MyProvider(props) {
  const { children, customStore } = props;

  return (
    <Provider store={customStore || store}>
      <Router>
        {children}
      </Router>
    </Provider>
  );
}
MyProvider.propTypes = {
  children: PropTypes.node,
  customStore: PropTypes.shape({}),
};
MyProvider.defaultProps = {
  children: null,
  customStore: null,
};

const wrapper = shallow(<MyComponent />, {
  wrappingComponent: MyProvider,
});
const provider = wrapper.getWrappingComponent();
provider.setProps({ customStore: mockStore });
```
