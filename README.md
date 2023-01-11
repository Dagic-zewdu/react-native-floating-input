# React Native Floating Label Input

## About The Package

 This is React Native package full customizable and its props extends from [React-native textinput props](https://reactnative.dev/docs/textinput#props). If you your label floats in the text input while focusing or in blur this is the perfect package and also multiple examples to full fill your expecations.💅🎉
## Getting Started

`npm install react-native-floating-inputs` 

or using yarn

`yarn add react-native-floating-inputs`

![screen shot](./screen-shot/screen-shot.gif)

# Props

* All react native [text input props](https://reactnative.dev/docs/textinput) are supported  in the input field. other than that the package have the following props

|             Prop              |     Type                     |                                                     Default                                                                                                                       |                                                                                                                                                 Description                                                                                                                                                  |
| :---------------------------: | :------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|         `labelProps`          |                  TextProps                    |                                                                                                                      undefined                                                                                                                      |                                                                                                                                    Set the label props as `TextProps`          
|     `Icon`        | JSX.Element       | Undefined     | Add left side Icon component.
|     `floatUpRange`        | JSX.Element       | 25     | Set the floatUp Range.
|     `rightIcon`        | JSX.Element       | Undefined     | Add right side component, it can be an icon..
|     `inputStyle`        | ViewStyle       | Undefined     | Set the input style.
|     `labelStyle`        | TextStyle       | Undefined     | Set the label style for the floating label component.
|     `labelColor`        | String       | '#111'     | Set the lable color.
|     `containerStyle`        | ViewStyle       | Undefined     | Set styles to the input container component.
|     `error`        | String       | Undefined     | Set your error message.

<p align="right">(<a href="#top">back to top</a>)</p>

# Usage

### Basic usage example

```ts
import {View, Text} from 'react-native';
import React, {useState} from 'react';
import FloatingLabelTextInput from 'react-native-floating-label-inputs';
// @ts-ignore
import Icon from 'react-native-vector-icons/EvilIcons';

export default function CommonExample() {
return (
<FloatingLabelTextInput
label="Name"
onChangeText={text => console.log(text)}
/>
);
}
```
### Lower Float Up Range

* `floatUpRange` is a prop that gives floating range starting from zero. You should assign the appropriate number depending on your container  height. the default value given is 25 but depending on your input container height it may vary.

<img src="https://raw.githubusercontent.com/Dagic-zewdu/react-native-floating-label-inputs/feature/examples/LowerFloatUpRange/photo.jpeg" width="65%" />

``` js
import {View, Text} from 'react-native';
import React from 'react';
import FloatingLabelTextInput from 'react-native-floating-label-inputs';

export default function LoweFloatUpRange() {
  return (
    <FloatingLabelTextInput
      label="Lower label"
      containerStyle={{height: 50}}
      floatUpRange={16}
      inputStyle={{marginTop: 5}}
      error="This field is required"
    />
  );
} 
```
### Different color depending on your style

* As this package is dynamic you can use own style, Their are 4 styling props to do this. `containerStyle` is responsible for the container that holds the text field. `inputStyle` is a style given to the texts that are typed by the user. `labelStyle` responsible for styling the lable and `lableColor` is color of the label. 

![](./examples/colored/photo.jpeg)

```ts
import {View, Text} from 'react-native';
import React from 'react';
import FloatingLabelTextInput from 'react-native-floating-label-inputs';

export default function ColoredExample() {
return (
<FloatingLabelTextInput
label="password"
containerStyle={{backgroundColor: '#111'}}
labelStyle={{backgroundColor: '#111'}}
labelColor="#fff"
inputStyle={{color: '#fff'}}
/>
);
}

```
- Using icon

Set an icon both to the right side (The first icon, which is displayed on the right side of the input field) and left side (The second icon, which is displayed on the left side of the input field)

<img src="https://raw.githubusercontent.com/Dagic-zewdu/react-native-floating-label-inputs/feature/examples/WithIcon/photo.jpeg" width="65%"/>

```js
import React, {useState} from 'react';
import FloatingLabelTextInput from 'react-native-floating-label-inputs';
//@ts-ignore
import FontisoIcon from 'react-native-vector-icons/Fontisto';
import FontAwesome5Icon from 'react-native-vector-icons/FontAwesome5';
function WithIcon() {
  const [showPassword, setShowPassword] = useState<boolean>(true);
  return (
    <FloatingLabelTextInput
      label="password"
      icon={
        <FontisoIcon
          name="locked"
          color="#111"
          size={20}
          onPress={() => console.log('Icon pressed')}
        />
      }
      rightIcon={
        !showPassword ? (
          <FontAwesome5Icon
            name="eye"
            color="#111"
            size={20}
            onPress={() => setShowPassword((s: boolean) => !s)}
          />
        ) : (
          <FontAwesome5Icon
            name="eye-slash"
            color="#111"
            size={20}
            onPress={() => setShowPassword((s: boolean) => !s)}
          />
        )
      }
      secureTextEntry={showPassword}
    />
  );
}

export default WithIcon;
```
- TextArea

A floating label for your `TextArea` field that can accept multiple lines of text. The label will float up a certain range (specified by the "floatUpRange" prop) as the user types. The "containerStyle" prop that sets the height of the container element, and an "inputStyle" prop that sets the height of the input field itself.

<img src="https://raw.githubusercontent.com/Dagic-zewdu/react-native-floating-label-inputs/feature/examples/textArea/photo.gif" />

 ```js
 import React from 'react';
import FloatingLabelTextInput from '../../src/floatingLabelTextInput';

export default function TextAreaExample() {
  return (
    <FloatingLabelTextInput
      label="Description"
      floatUpRange={50}
      containerStyle={{height: 100}}
      inputStyle={{height: 100}}
      multiline={true}
    />
  );
}
 ```
- Border Bottom With an icon

<img src="https://raw.githubusercontent.com/Dagic-zewdu/react-native-floating-label-inputs/feature/examples/borderBottomWithIcon/photo.jpeg" width="65%"/>

``` js
import React, {useState} from 'react';
import FloatingLabelTextInput from '../../src/floatingLabelTextInput';
import FontAwesome5Icon from 'react-native-vector-icons/FontAwesome5';
import FontisoIcon from 'react-native-vector-icons/Fontisto';

export default function BorderBottomWithIcon() {
  const [showPassword, setShowPassword] = useState<boolean>(true);

  return (
    <FloatingLabelTextInput
      label="Password"
      containerStyle={{
        borderWidth: 0,
        backgroundColor: '#f5f0e1',
        borderBottomWidth: 1,
        height: 40,
      }}
      labelStyle={{backgroundColor: '#f5f0e1'}}
      floatUpRange={16}
      icon={
        <FontisoIcon
          name="locked"
          color="#111"
          size={20}
          onPress={() => console.log('Icon pressed')}
        />
      }
      rightIcon={
        !showPassword ? (
          <FontAwesome5Icon
            name="eye"
            color="#111"
            size={20}
            onPress={() => setShowPassword((s: boolean) => !s)}
          />
        ) : (
          <FontAwesome5Icon
            name="eye-slash"
            color="#111"
            size={20}
            onPress={() => setShowPassword((s: boolean) => !s)}
          />
        )
      }
      secureTextEntry={showPassword}
    />
  );
}
<p align="right">(<a href="#top">back to top</a>)</p>

```


## support us
[☕  Buy me a coffee](https://www.buymeacoffee.com/dagizewdudc)

- You can also give as star to our repo.
## Authors

### Author 1

👤 **Dagmawi Zewdu**

 - GitHub: [@Dagic-zewdu](https://github.com/Dagic-zewdu)
- LinkedIn: [Dagi-Zewdu](https://www.linkedin.com/in/dagic-zewdu/)

### Author 2

👤 **Sentayhu Berhanu**

- GitHub: [@sentayhu19](https://github.com/sentayhu19)
- LinkedIn: [sentayhu-berhanu](https://www.linkedin.com/in/sentayhu-berhanu-6376579a/)

<!-- CONTRIBUTING -->
## Contribution

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>



### Built With

* [React Native](https://reactnative.dev/)
* [TypeScript](https://www.typescriptlang.org/)
* [JavaScript](https://www.javascript.com/)

 

