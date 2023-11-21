it is a collection of react component, gives you special react component, those components are then compiled to build for IOS and Android platforms.

In react native only the UI elements are compiled, where as the logic of the JavaScript code is not compiled, instead a JavaScript thread hosted by React Native.

### View component

This component is only used to hold other component never use it to render a content in your application.

It acts as a container component used to hold other components.

No Direct CSS support, but we can add CSS properties using props using JavaScript Objects.

To add CSS to the project we need another module called StyleSheet from react-native.

```jsx
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center",
  },
  textStyle: {
    margin: 20,
    borderWidth: 2,
    borderColor: "blue",
    padding: 10,
  },
});
```

> Note : In flex box justify content is for the main axis, where as alignItems property is for cross axis.

Button element does not have a style property.

Style do not cascade unlike web-development CSS.

## ScrollView

It is a component in react native that provides scrollable view for displaying a large content that may not fit entirely within the visible area of the screen. It allows users to scroll through the content horizontally or vertically.

ScrollView must have a bound height in order to work, since they contain unbounded-height children into a bounded container.

alwaysBounceVertically

The scroll view bounces vertically when it reaches the end , even if the content is smaller than the scroll itself.

There exist a great drawback to scroll view, because it rendered all its items, when the UI is rendered, User might all the items to be rendered on the view at a particular time, this creates an performance issue in app, suppose we are required to display a list of 10,000 items and rendered all those items before rendering is a resource intensive task.

## FlatList

It is also a component in react native used to provide scrollable content, Effective for rendering large lists of data.

It is commonly used in a situation where we need to display a very long list.

Uses Lazy loading : rendering only those items which are visible or will be visible to the user in the future.

data : we specify the data which the flatList will hold .

renderItem : It is a function prop that you provide to specify how each item in your data should be rendered as a React element.

keyExtractor : It is a function that you can provide to specify how to extract unique key from each item in your provided data, Because there may be some cases where you data may not provide a specific well defined key in the data.

## Pressable

It is a built in component and provide interactive behavior to its child components. It’s used to wrap other components and add touch-based functionality like handling press , long press and other touch events.

style : This prop of Pressable is used to apply visual styling to the pressable component

```tsx
<Pressable
      onPress={handlePress}
      style={({ pressed }) => [
        {
          backgroundColor: pressed ? 'lightgray' : 'blue',
          borderRadius: 5,
          padding: 10,
        },
        pressed && { opacity: 0.5 }, // Reduce opacity when pressed
      ]}
    >
```

when a component is pressed the pressed property is true.

## Modal

It is a UI component which is used to display content on the top of the current screen in a modal or pop-like menu .

They are often used to display alerts or ask user input .

```tsx
import React, { useState } from "react";
import { View, Text, Modal, Button } from "react-native";

function MyModal() {
  const [modalVisible, setModalVisible] = useState(false);

  const openModal = () => {
    setModalVisible(true);
  };

  const closeModal = () => {
    setModalVisible(false);
  };

  return (
    <View>
      <Button title="Open Modal" onPress={openModal} />
      <Modal
        visible={modalVisible}
        animationType="slide" // You can specify the animation type
        transparent={true} // Make the modal background transparent
      >
        <View>
          <Text>Modal Content</Text>
          <Button title="Close Modal" onPress={closeModal} />
        </View>
      </Modal>
    </View>
  );
}

export default MyModal;
```

> We can also pass array of style objects in style prop of react components.
>
> ```tsx
> style={({ pressed }) => [
>           pressed
>             ? [styles.pressed, styles.outerContainer]
>             : styles.outerContainer
>         ]}
> ```

## Linear Gradient

expo has a special component called `<LinearGradient/>` which is used to get Gradient colors.

### Safe Area View

It is the component provided by the React Native which is used to make sure that content is within the device display screen.

Safe area is the portion of the screen that is not covered with status bar, camera bar and etc.

## Custom fonts

We can use usefonts hook to load some custom fonts in our app .

`expo install expo-font`

It also returns an array which contains a value which return a Boolean value that weather the fonts have been loaded or not.

```tsx
const [fontsLoaded] = useFonts({
  "open-sans": require("./assets/fonts/open-sans.ttf"),
  "open-sans-r": require("./assets/fonts/open-sans-2.ttf"),
});
```

> when we set `width = '%80'` then this width is according to the 80% of the parent container.

### Dimensions

This is a API build into react-native library.
It is not a component but a java script object

To the device dimensions we do :

```tsx
const deviceWidth = Dimensions.get("window").width;
const deviceHeight = Dimensions.get("window").height;
```

`.get('window')` vs `.get('screen')`

In case of IOS both means the same.
In case of Android window means only the display area excluding the status bar of the mobile screen, where as screen in android means the display area including the status bar of the mobile screen.

## Screen orientation

The screen orientation is specified in the `app.json` file in the home directory.
`"orientation": "portrait",`
To make the app for both orientation we can do
`"orientation" : "default"`,

#### useWindowDimensions

This hook automatically updates the height and width or font size when the screen size changes.
`const { height, width } = useWindowDimensions()`

### KeybordAvoidingView

Will automatically adjust the height, position or bottom based on the keyboard remains visible while virtual keyboard is displayed.

```tsx
     <KeyboardAvoidingView
        style={styles.screen}
        behavior={Platform.OS === 'ios' ? 'padding' : 'height'}
      >
```

It prevent the content from being hidden behind the keyboard.

**Behavior** : This prop tells how to react to the presence of keyboard.

## Platform

[Click Here](https://reactnative.dev/docs/platform)

It is an API built in react native.
It has multiple props you check out them here

**Example** : <br>
Suppose you want to change the borderWidth property, according to the Platform :

1. **Conditional statement** : `borderWidth: Platform.OS === 'android' ? 2 : 0`
2. **Platform.select()** : Returns the most fitting value for the platform you are currently running on <br>`borderWidth: Platform.select({ ios: 0, android: 2 }),`<br>

##### Status bar

Component used to control the app's status bar. Typically at the top of the screen, that display the time and battery percentage and Cellular information, other status icons.<br>
<span style='color:DodgerBlue;font-weight:bold;'>Has a style arguemnt</span> used to set the dark and light mode for the status-bar.

### React Navigation

Native Stack Navigator provides a way for your app to transition between screens where each new screen is placed on top of a stack.

```tsx
import { NavigationContainer } from "@react-navigation/native";
import { createNativeStackNavigator } from "@react-navigation/native-stack";
```

```tsx
const Stack = createNativeStackNavigator();
```

> This will create an object of createNativeStackNavigator.

```tsx
<NavigationContainer>
  <Stack.Navigator>
    <Stack.Screen name="MealsCategories" component={CategoryScreen} />
    <Stack.Screen name="MealsOverView" component={MealOverviewScreen} />
  </Stack.Navigator>
</NavigationContainer>
```

> Wrap the main component within the NavigationContainer

**useNavigation** : we can use to get access to the navigation object.<br>
useful when we cannot pass the navigation prop into the component directly.<br>

```tsx
interface RootStackParamList {
  MealsOverView: {
    categoryId: number;
  };
}

const navigation =
  native.useNavigation<
    native.NavigationProp<RootStackParamList, "MealsOverView">
  >();

navigation.navigate("MealsOverView", {
  categoryId: parseInt(item.id, 10),
} as any);
```

#### Passing Data

We can also pass data with the useNavigation hook with built in route prop.

```tsx
navigation.navigate("MealsOverView", {
  categoryId: item.id,
} as any);
```

here categoryId is sent as a parameter to the MealsOverView screen.

```tsx
type props = NativeStackScreenProps<RootStackParams, "MealsOverView">;
```

`{ route }: props`<br>
**Access the parameter like this:** <br>
`{route.params.categoryId}`

### Options Stack Navigator

To configure each Stack Screen in we can use options argument.<br>
[Options](https://reactnavigation.org/docs/stack-navigator/)

**To configure the entire Stack Navigator**, there is an arguemnt called screenOptions which will set the options for entire multiple stack screen nested into Stack Navigator.

```tsx
<Stack.Navigator
          screenOptions={{
            headerStyle: { backgroundColor: '#350401' },
            headerTintColor: 'white',
            contentStyle: { backgroundColor: '#3f2f25' }
          }} >
```

here we can put all the options that we want in all the stack screens.

<span style='color:SlateBlue;'>In case of override of options,</span> options in the specific Stack screen will be considered.<br>

#### useEffect & useLayoutEffect

- Does the similar thing.
- **useLayoutEffect** is called before the user can see the visual changes, where as **useEffect** will be called after the user is able to see the visual changes.<br>

> Type definition ( typescript ) for vector icon in react native <br> `icon: keyof typeof Ionicons.glyphMap`

#### React Native Drawer

**Snippet** : <br>

```tsx
<Drawer.Navigator
  screenOptions={{
    headerStyle: { backgroundColor: "#3c0a6b" },
    headerTintColor: "white",
    drawerActiveBackgroundColor: "#f0e1ff",
    drawerStyle: {
      backgroundColor: "#ccc",
    },
  }}
>
  <Drawer.Screen
    name="Welcome"
    component={WelcomeScreen}
    options={{
      drawerLabel: "Welcome Screen",
      drawerIcon: ({ color }) => <Ionicons name="home" color={color} />,
    }}
  />
  <Drawer.Screen
    name="User"
    component={UserScreen}
    options={{
      drawerLabel: "User Screen",
      drawerIcon: ({ color }) => <Ionicons name="skull" color={color} />,
    }}
  />
</Drawer.Navigator>
```

> The drawerIcon accepts a function which returns a React Node when some parameters like <span style='color:MediumSeaGreen'>color,focused,size</span> is given.

> In Stack Navigator the option to color the content is `contentStyle = {}`, where as in Drawer Navigator the option to color the content is `sceneContainerStyle: { backgroundColor: '#350401' },`

> In javascript `getMonth()` method returns month number with 0 based indexing, make sure to add 1 to it.

#### React Navigation

- The `Navigator` have a special property called **screen options**.
- Contains the configuration for all the screens present inside it.
- The screen options also receive the navigation prop  reference like 👇.

```tsx
 screenOptions={({ route, navigation }) => ({
    title: route.params.title,
  })}
```

> To convert a expression to boolean expression we can do `const isEditing = !!editExpenseId;`.




