# React Native Workshop

# Welcome!

Hello! And welcome to this React Native workshop! We'll spend the next 2.5 hours taking a look at what React Native is, quickly looking at the tools we'll be using, then diving right into building a project. This is an introductory workshop aimed at helping you familiarize yourselves with React Native. More advanced workshops are in the works and will be offered in the upcoming months.

Please do ask questions if you have any, but do keep in mind that if its not directly relevant to what we're working on, we may have to hold off chatting about it until the end of the workshop to make sure we get through all the content.

# What is React?

React is a JavaScript library for building user interfaces. It allows you to build encapsulated components that manage their own state, then compose them to make complex UIs. React by default renders client-side, but can also render on the server using Node, and power mobile apps using React Native.

# Quick intro to React Native

React Native is a library that allows you to create native apps for Android and iOS using React JS. You can use React Native in an existing Android or iOS project, or build an entire app from the ground up using React Native. Today we'll be doing the latter!

The important thing to remember here is that the app we build will be a truly native app. Other libraries have offered the "use web tech to build apps" ability before, but they embed a webview (think iframe) into a native shell, and render your app within. This leads to poor performance and not a true native experience.

# Tooling

## JavaScript + React

We'll be writing lots of regular and React-style JavaScript today!

## React Native

Obviously

## Expo

Expo is a framework, or a set of tools and services, that allow you to build, deploy and quickly iterate on React Native apps. The developer experience is super nice. We'll get into this soon.

# Requirements + Pre-requisites

## Xcode

Please be on the latest version of Xcode. (Xcode 11.X at the time of writing)

## Node

Verify and/or install the latest stable version of Node.js


``` Bash
brew install node

# or
brew update
brew upgrade node
```

## Expo CLI

Next, install the Expo CLI globally by running the following command. You can also run the same command to update your version of the `expo-cli`.

``` Bash
npm install -g expo-cli
```

## Expo client app

Install the "Expo" client app on your iOS or Android device and create an account. Log into your account in your terminal window by running


``` Bash
expo login
```

# JavaScript in 5ish minutes

Since not everyone here is familiar with JS, lets take a few minutes to go through some fundamental concepts. These will be sufficient to get started, and we'll add more as necessary throughout the workshop.

## Variables

Variables are declared in two ways: either use `const` (for constants), or `let` (for variables that can change over time).

You can use single, double, and back-ticks to create string literals, only back-ticks can interpolate variables though.

``` JavaScript
const name = "Haris";

console.log("Hello " + name);
console.log('Hello ' + name);
console.log(`Hello ${name}`);
```

Use square brackets `[]` to create arrays.


``` JavaScript
const exampleArray = [7, 14, 21];
```

Use curly brackets `{}` to create objects (string indexed dictionaries).

``` JavaScript
const exampleObject = {
  name: "Haris",
  role: "Senior Engineer",
  employer: "Shopify",
  coworkers: ["Ryan", "Sergey", "Alex"],
  somethingElse: {
    nested: true
  }
}
```

## Functions

There are two main ways to create a function: the `function` keyword or the arrow syntax `=>`. Arrow functions can directly return a value from the expression without needing the explicit `return` keyword.

``` JavaScript
// with function keyword
function example() {
  return "This is fun"
}

// with arrow syntax
const example = () => {
  return "This is fun"
}

// can be simplified and rewritten as
const examples = () => "This is fun"

// returned objects must be in `()`
const example = () => {
  return (
    {name: "Haris"}
  )
}

// can be simplified and rewritten as
const example = () => ({name: "Haris"})

// with function keyword and 1 param
function double(num) {
  return num * 2;
}

// with arrow syntax
const double = (num) => num * 2;

// simplify since we only have 1 param
const double = num => num * 2;
```

# Create a New React Native App

Lets get started by creating a new React Native app using Expo!

Run `expo init` to create a new project. Expo provides a number of template options to get started with. You'll also notice the templates grouped into to workflow types: Managed and Bare.

## Workflow types

With the managed workflow you only write JavaScript / TypeScript, and Expo tools + services take care of the rest for you. This is similar to "Rails" and "Create React App" for React Native.

In the bare workflow you have full control over every aspect of the native project, and Expo tools can't help quite as much.

You can begin a project using the managed workflow, but "eject" into a bare workflow at anytime. However, you *cannot* go in reverse.

We'll stick with the "blank" template in the managed workflow for this workshop. Continue the setup by entering a project name and slug, and say "yes" to install dependencies using Yarn.

Note: The Arrive team opted to not use Expo at all. We wanted an absolute bare bones experience to really understand every aspect as we were vetting whether React Native was a viable choice. We were also using a number of native modules that Expo would not support, so we knew off the bat that a managed workflow would be impossible to use without sacrificing features.

# Running a React Native app

Navigate into the project directory and start expo.

``` Bash
cd [project-name]
expo start
```

This will open the Metro Bundler screen in a new tab in your browser.

Click the 'Run on iOS simulator' or hit the `i` key in your terminal to boot up an iOS simulator, install the expo client on it and start your app. This will trigger Metro Bundler to build your app and serve it.

Congratulations on getting your first React Native mobile app up and running!

## Expo client app

You can also follow the instructions in the terminal for getting the app running on your mobile device using the previously installed Expo client. Let's go through this together now to make sure we can all test on our personal devices.

if you haven't already, log into your Expo account in the terminal using:


``` Bash
expo login
```

App QR codes and links can be sent to anyone to test your app. As long as Expo is running on your machine, anyone can scan the code / add the link to their Expo client and test the app.

# Basic components

## View

The `View` component is equivalent to `uiview` in iOS, `view` in Android, and a `div` in web. Its one of the simplest and most used components in React Native. It is used to create layout, but can also be used to create basic shapes like squares, rectangles and circles. `View` components are not "visible" as they do not have visual representations. You will often wrap other elements inside `View` components to implement layout and styling.

In web, we also have other semantic elements, such as `header`, `section`, `footer`, etc. These are all replaced with `View` in React Native.

[https://facebook.github.io/react-native/docs/view](https://facebook.github.io/react-native/docs/view)

## Text

The `Text` component handles *all* textual elements in React Native. All text must be wrapped in a `Text` component.

[https://facebook.github.io/react-native/docs/text](https://facebook.github.io/react-native/docs/text)

## Image

The `Image` component allows you to render an image. You tell the component to render a specific image by passing in an image object to the `source` prop.

[https://facebook.github.io/react-native/docs/image](https://facebook.github.io/react-native/docs/image)

## TouchableOpacity

A wrapper for making views respond properly to touches. On press down, the opacity of the wrapped view is decreased, dimming it. It also takes a value for the `onPress` prop.

[https://facebook.github.io/react-native/docs/touchableopacity](https://facebook.github.io/react-native/docs/touchableopacity)

## ScrollView

Similar to the `View` component, except that it implements scrolling when its content is too long. The `View` component cannot be scrolled. Scrolling is vertical by default, but can be switched to horizontal by passing in the `horizontal` prop. ScrollViews are not super performant when content is too long and complex.

[https://facebook.github.io/react-native/docs/scrollview](https://facebook.github.io/react-native/docs/scrollview)

# Styling

To style React Native apps, we use css-in-js, essentially writing CSS in a JS format. We'll play around with a bunch of styling over the course of this workshop. Styles are passed to a component through the `style` prop. There are two main ways styles can be applied: inline and by using the `StyleSheet` api.

## Inline styles

Inline styles are applied passing in an object of key-value pairs to the `style` prop directly.


``` JavaScript
<Text style={{color: 'red'}}>This text will be red</Text>
```

## StyleSheet

Applying all your styles inline can get really messy very quickly. So I recommend you use the `StyleSheet` api provided by React Native. See the following example to understand how its used.

``` JavaScript
<Text style={styles.example}>This text will be red</Text>

const styles = StyleSheet.create({
  example: {
    color: 'red'
  }
})
```

The `styles` object will continue to grow as new keys are added to represent various 'classes'.

[https://facebook.github.io/react-native/docs/stylesheet](https://facebook.github.io/react-native/docs/stylesheet)

## Style arrays

Similar to how you can apply multiple classes to elements in HTML, you can pass in an array of styles into the style prop.

``` JavaScript
<Text style={[styles.one, styles.two]}>This text will be red</Text>

const styles = StyleSheet.create({
  one: {
    color: 'blue'
  },
  two: {
    color: 'red'
  }
})
```

## Layout with Flexbox

Layout is achieved through Flexbox. CSS Grids, tables and floats are not available.

Some fundamentals:

- Flexbox requires there to be a container element (the flex container) and elements inside (the flex children)
- Styles applied to the container tell it how its content will flow. We aren't worried about individually placing elements, rather how all the content will behave/flow inside the flex container. For example, left to right, or top to bottom, spaced out evenly, or all bunched up together.
- The direction of flow for a flex container is defined using the `flexDirection` property. This also defines your primary axis. Your cross axis becomes your secondary axis. The default value for `flexDirection` is `column`, which causes your content to flow from top to bottom. Note: the default value on web is `row`.
- `justifyContent` controls how items are distributed on the primary axis.
- `alignItems` controls how items are distributed on the cross/secondary axis.

For those new to Flexbox, I recommend you watch a video or two to familiarize yourselves with some of the more complex aspects of Flexbox. There are quite a number of properties and they can get confusing pretty quick.

# Conference app: Home Screen

Alright! Enough basics! Let's build our first screen: the Home Screen.

First, create a new folder in the root directory and name it `screens`. This is where our HomeScreen and other screen files will go. It keeps things neat and tidy.

Create a new file in the `screens` directory and call it `HomeScreen.js`.

Setup this file by creating a new functional component named `HomeScreen` , setting up initial imports, and add some temporary text to test things out.


``` JavaScript
import React from "react";
import {Text, View} from "react-native";

const HomeScreen = () => {
  return (
    <View>
      <Text>This is the Home Screen!</Text>
    </View>
  );
};

export default HomeScreen;
```

This is great, but you'll notice that our app doesn't render this component we created. To do so, we need to import this component into our `App.js` file, and `return` it in the `App()` function's `render`.

``` JavaScript
import React from "react";
import { StyleSheet, Text, View } from "react-native";
import HomeScreen from "./screens/HomeScreen";

export default function App() {
  return (
    <View style={styles.container}>
      <HomeScreen />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center"
  }
});
```

Woop woop!

Alright, let's head back to the Home screen. This screen will consist of the app's title, an image (branding perhaps), some additional text, and a button. Import the necessary components from the React Native library, and add them to the screen.


``` JavaScript
import React from "react";
import { Text, View, TouchableOpacity, Image } from "react-native";

const HomeScreen = () => {
  return (
    <View>
      <Image />
      <Text>RNCONF</Text>
      <Text>The best React Native conference, powered by Shopify</Text>

       <TouchableOpacity>
         <Text>See schedule</Text>
       </TouchableOpacity>
    </View>
  );
};

export default HomeScreen;
```

Now let's get the image in place. Copy the provided `react.png` file into the `assets` folder. To use this image, first import it (you can give it any name you like).

``` JavaScript
import Icon from "../assets/react.png";
```

Then pass it into the `source` prop for the `Image` component.

``` JavaScript
<Image source={Icon} />
```

Great! We've now got all our content in place for this screen, but its looking pretty rough. Let's fix it up a bit with some styles. Import `StyleSheet` from `react-native`, create a styles object using the `StyleSheet` API and write out the various styles we'll need for the text elements. Then pass in the appropriate styles to various components using the `style` prop.

Check out `flatuicolors` for help with picking colors! [https://flatuicolors.com/](https://flatuicolors.com/)

``` JavaScript
const HomeScreen = () => {
  return (
    <View style={styles.container}>
      <Image style={styles.image} source={Icon} />
      <Text style={styles.appName}>RNCONF</Text>
      <Text style={styles.description}>
        The best React Native conference, powered by Shopify
      </Text>

      <TouchableOpacity style={styles.button}>
        <Text style={styles.buttonText}>See schedule</Text>
      </TouchableOpacity>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff",
    alignItems: "center",
    justifyContent: "center",
    paddingHorizontal: 24
  },
  image: {
    width: 70,
    height: 70,
    marginBottom: 8
  },
  appName: {
    fontSize: 60,
    fontWeight: "700",
    color: "#222f3e"
  },
  description: {
    paddingHorizontal: 48,
    textAlign: "center",
    marginBottom: 48,
    color: "#576574"
  },
  button: {
    backgroundColor: "#5f27cd",
    paddingHorizontal: 16,
    paddingVertical: 8,
    borderRadius: 4
  },
  buttonText: {
    color: "white"
  }
});
```

We won't cover it in this workshop, but if you're interested in setting up a custom font: [https://docs.expo.io/versions/latest/guides/using-custom-fonts/](https://docs.expo.io/versions/latest/guides/using-custom-fonts/)

Excellent! We've pretty much completed our first screen! Let's move on to the second.

# Conference app: Detail Screen

The details screen will show details for a specific talk during the conference. It will show the talk's title, time, description, and show the name, photo and job title of the speaker.

Let's create a new file in the `screens` folder and call it `DetailsScreen.js`.

Then setup the functional component and the default export, along with some imports we know we're going to use (View and Text components)


``` JavaScript
import React from "react";
import { View, Text } from "react-native";

const DetailsScreen = () => {
  return (
    <View>
      <Text>Details Screen</Text>
    </View>
  );
};

export default DetailsScreen;
```

To preview this screen, import it in `App.js` and render it instead of the `HomeScreen`.

Use this moment to also simplify the container styles as we no longer need most of them at the App level, since we're applying styles to individual screens directly.

``` JavaScript
import React from "react";
import { StyleSheet, View } from "react-native";
import HomeScreen from "./screens/HomeScreen";
import DetailsScreen from "./screens/DetailsScreen";

export default function App() {
  return (
    <View style={styles.container}>
      <DetailsScreen />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1
  }
});
```

Back in the `Details` screen, add the necessary structure and content. Add the various `Text` components needed for the title, date & time, description, speaker name, job title, and an `Image` for the speaker's headshot. You should have something that looks similar to this.


``` JavaScript
import React from "react";
import { View, Text, Image } from "react-native";

const DetailsScreen = () => {
  return (
    <View>
      <View>
        <Text>Talk title</Text>
        <Text>Date & time</Text>
        <Text>Talk description Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris varius
          nisl sapien, a ullamcorper felis aliquam nec. Aliquam erat volutpat.
          Donec eget risus pretium orci fermentum aliquam et pellentesque sem.
          Maecenas luctus dictum odio, imperdiet pharetra felis accumsan quis.
          Integer lobortis augue felis. Ut non dui gravida, luctus lectus non,
          semper lectus.</Text>
      </View>
      <View>
        <Image />
        <View>
          <Text>Speaker name</Text>
          <Text>Job title</Text>
        </View>
      </View>
    </View>
  );
};

export default DetailsScreen;
```

Excellent, now let'ss work in some styles.


``` JavaScript
const DetailsScreen = () => {
  return (
    <View style={styles.container}>
      <View style={styles.talkDetails}>
        <Text style={styles.title}>Talk title</Text>
        <Text style={styles.time}>Date & time</Text>
        <Text style={styles.description}>
          Talk description Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris varius
          nisl sapien, a ullamcorper felis aliquam nec. Aliquam erat volutpat.
          Donec eget risus pretium orci fermentum aliquam et pellentesque sem.
          Maecenas luctus dictum odio, imperdiet pharetra felis accumsan quis.
          Integer lobortis augue felis. Ut non dui gravida, luctus lectus non,
          semper lectus.
        </Text>
      </View>
      <View style={styles.speaker}>
        <Image
          style={styles.avatar}
          source={{ uri: "https://i.picsum.photos/id/365/80/80.jpg" }}
        />
        <View>
          <Text style={styles.speakerName}>Speaker name</Text>
          <Text style={styles.speakerRole}>Job title</Text>
        </View>
      </View>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1
  },
  talkDetails: {
    paddingVertical: 48,
    paddingHorizontal: 24,
    borderBottomWidth: StyleSheet.hairlineWidth,
    borderBottomColor: "#ccc"
  },
  title: {
    fontSize: 36,
    fontWeight: "700"
  },
  time: {
    fontWeight: "700",
    marginTop: 16
  },
  description: {
    marginTop: 8
  },
  speaker: {
    padding: 16,
    borderRadius: 8,
    shadowOffset: { width: 0, height: 15 },
    shadowOpacity: 0.25,
    shadowRadius: 28,
    elevation: 3,
    shadowColor: "#000",
    flexDirection: "row",
    backgroundColor: "#fff",
    marginTop: 24,
    marginHorizontal: 24,
    alignItems: "center"
  },
  avatar: {
    height: 80,
    width: 80,
    borderRadius: 80,
    marginRight: 16
  },
  speakerName: {
    fontSize: 16,
    fontWeight: "700",
    marginBottom: 4
  },
  speakerRole: {
    fontSize: 11
  }
});
```

Dimensions are normalized to logical units. So a thickness of `1` can look different (will look like 3 units wide on a super retina display), so we can use `StyleSheet.hairlineWidth` instead.

And we're done! On to the next screen!

# Conference app: Schedule Screen

The schedule screen will show a list of all the talks during the conference. It'll list the talk's name, and when it starts.

## New components: `FlatList` and `SectionList`

Before diving in, let's cover two new components React Native provides: `FlatList` and `SectionList`. These two components are built on top of `ScrollView`, so they have all the same benefits. They also have further optimizations to handle super long lists. They do this primarily by avoiding rendering things that are out of view.

Consider a grocery list app. If you wanted to show a list of all items without any grouping, you'd utilize a `FlatList`. Now let's say you wanted to show that same list but organized in different categories, or sections: Fruits, Vegetables, Cleaning, Misc. Here, you'd use a `SectionList` instead.

Back to the conference app: We could render a list that shows all the talk names and times in one giant list, but it'd make more sense to organize it by time. So, we'll be using a `SectionList` with the talk times representing the section headings/titles.

## Building the `SectionList`

Create a new file in the `screens` directory and call it `ScheduleScreen.js` and add some basic setup. Adjust the `App.js` screen to render the `ScheduleScreen` component instead. (Similar to what we did for the Details Screen work).


``` JavaScript
// ScheduleScreen.js

import React from "react";
import { View, Text } from "react-native";

const ScheduleScreen = () => {
  return (
    <View>
      <Text>Schedule Screen</Text>
    </View>
  );
};

export default ScheduleScreen;

// App.js

import React from "react";
import { StyleSheet, View } from "react-native";
import HomeScreen from "./screens/HomeScreen";
import DetailsScreen from "./screens/DetailsScreen";
import ScheduleScreen from "./screens/ScheduleScreen";

export default function App() {
  return (
    <View style={styles.container}>
      <ScheduleScreen />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1
  }
});
```

Import the `SectionList` component from `react-native` and render one in the `ScheduleScreen` component.


``` JavaScript
import React from "react";
import { View, Text, SectionList } from "react-native";

const ScheduleScreen = () => {
  return (
    <View>
      <Text>Schedule Screen</Text>
      <SectionList />
    </View>
  );
};

export default ScheduleScreen;
```

## Required props: `sections` and `renderItem`

A `SectionList` has two required props: `sections` and `renderItem`. `sections` expects an array of data, broken up by sections. `renderItem` expects a function that will render **every** item in **every** section.

Our mock data is available in the provided `mockdata.js` file. Add this file to the root of your project directory. We can now import the `mockData` array from `mockData.js` and pass it to the `SectionList`'s `sections` prop.


``` JavaScript
import React from "react";
import { View, Text, SectionList } from "react-native";
import { mockData } from "../mockData";

const ScheduleScreen = () => {
  return (
    <View>
      <Text>Schedule Screen</Text>
      <SectionList sections={mockData} />
    </View>
  );
};

export default ScheduleScreen;
```

Now create a function responsible for rendering each item in each section. This function will receive a bunch of data from the `SectionList`. Include that as an expected parameter.


``` JavaScript
const singleItem = data => {
  return (
    <View>
      <Text>Single Item</Text>
    </View>
  );
};

const ScheduleScreen = () => {
  return (
    <View>
      <Text>Schedule Screen</Text>
      <SectionList sections={mockData} renderItem={singleItem} />
    </View>
  );
};
```

Excellent! Now use the received `data` to pull out actual information rather than rendering "Single Item" every time.


``` JavaScript
const singleItem = data => {
  const item = data.item;

  return (
    <View>
      <Text>{item.title}</Text>
    </View>
  );
};
```

## Optional props

A `SectionList` has a number of optional props.

### keyExtractor

`keyExtractor` expects a function, which is used to extract a unique key for a given item. The Key is used for caching and to keep track of re-ordering.

``` JavaScript
..

const keyExtractor = item => item.id;

const ScheduleScreen = () => {
  return (
    <View>
      <Text>Schedule Screen</Text>
      <SectionList
        sections={mockData}
        renderItem={singleItem}
        keyExtractor={keyExtractor}
      />
    </View>
  );
};
```

### ItemSeparatorComponent

Rendered between each item, but not at the top or bottom. Import `StyleSheet` from `react-native`, create a new styles object, add some divider styles, and create a divider component.

``` JavaScript
..
import { View, Text, SectionList, StyleSheet } from "react-native";
..

const divider = () => {
  return <View style={styles.divider} />;
};

const ScheduleScreen = () => {
  return (
    <View>
      <Text>Schedule Screen</Text>
      <SectionList
        sections={mockData}
        renderItem={singleItem}
        keyExtractor={keyExtractor}
        ItemSeparatorComponent={divider}
      />
    </View>
  );
};

const styles = StyleSheet.create({
  divider: {
    width: "100%",
    height: 2,
    backgroundColor: "#eee"
  }
});
```

### renderSectionHeader

Rendered at the top of each section. These stick to the top of the `ScrollView` by default on iOS. Explore the  `stickySectionHeadersEnabled` prop to change this behavior.

Add some styles to separate these headers out from the other items.

``` JavaScript
..

const sectionHeader = data => {
  const section = data.section;
  return (
    <View style={styles.sectionHeader}>
      <Text style={styles.sectionHeaderText}>{section.time}</Text>
    </View>
  );
};

const ScheduleScreen = () => {
  return (
    <View>
      <Text>Schedule Screen</Text>
      <SectionList
        sections={mockData}
        renderItem={singleItem}
        keyExtractor={keyExtractor}
        ItemSeparatorComponent={divider}
        renderSectionHeader={sectionHeader}
      />
    </View>
  );
};

const styles = StyleSheet.create({
  divider: { .. },
  sectionHeader: {
    backgroundColor: "#5f27cd",
    paddingHorizontal: 16,
    paddingVertical: 12
  },
  sectionHeaderText: {
    fontWeight: "700",
    color: "white"
  },
});

..
```

### ListHeaderComponent

Rendered at the very beginning of the list. Add some styles here too.

``` JavaScript
..

const listHeader = () => {
  return (
    <View style={styles.listHeader}>
      <Text style={styles.listHeaderText}>Schedule</Text>
    </View>
  );
};


const ScheduleScreen = () => {
  return (
    <View>
      <Text>Schedule Screen</Text>
      <SectionList
        sections={mockData}
        renderItem={singleItem}
        keyExtractor={keyExtractor}
        ItemSeparatorComponent={divider}
        renderSectionHeader={sectionHeader}
        ListHeaderComponent={listHeader}
      />
    </View>
  );
};

const styles = StyleSheet.create({
  divider: { .. },
  sectionHeader: { .. },
  sectionHeaderText: { .. },
  listHeader: {
    backgroundColor: "#ccc",
    paddingVertical: 32,
    paddingHorizontal: 20,
    justifyContent: "center",
    alignItems: "center"
  },
  listHeaderText: {
    fontSize: 24,
    fontWeight: "600"
  }
});

..
```

Lastly, add styles for the individual talk items, add container styles, and remove the temporary `Text` component we originally started with.

``` JavaScript
const singleItem = data => {

  const item = data.item;
  return (
    <View style={styles.singleItem}>
      <Text>{item.title}</Text>
    </View>
  );
};

..

const ScheduleScreen = () => {
  return (
    <View style={styles.container}>
      <SectionList
        sections={mockData}
        renderItem={singleItem}
        keyExtractor={keyExtractor}
        ItemSeparatorComponent={divider}
        renderSectionHeader={sectionHeader}
        ListHeaderComponent={listHeader}
      />
    </View>
  );
};

..

const styles = StyleSheet.create({
  divider: { .. },
  sectionHeader: { .. },
  sectionHeaderText: { .. },
  listHeader: { .. },
  listHeaderText: { .. },
  singleItem: {
    paddingHorizontal: 16,
    paddingVertical: 20
  },
  container: {
    flex: 1,
    backgroundColor: "#fff"
  },
});
```

### Final code

Your final code for `ScheduleScreen` should something like this:

``` JavaScript
import React from "react";
import { View, Text, SectionList, StyleSheet } from "react-native";
import { mockData } from "../mockData";

const singleItem = data => {
  const item = data.item;

  return (
    <View style={styles.singleItem}>
      <Text>{item.title}</Text>
    </View>
  );
};

const keyExtractor = item => item.id;

const divider = () => {
  return <View style={styles.divider} />;
};

const sectionHeader = data => {
  const section = data.section;
  return (
    <View style={styles.sectionHeader}>
      <Text style={styles.sectionHeaderText}>{section.time}</Text>
    </View>
  );
};

const listHeader = () => {
  return (
    <View style={styles.listHeader}>
      <Text style={styles.listHeaderText}>Schedule</Text>
    </View>
  );
};

const ScheduleScreen = () => {
  return (
    <View style={styles.container}>
      <SectionList
        sections={mockData}
        renderItem={singleItem}
        keyExtractor={keyExtractor}
        ItemSeparatorComponent={divider}
        renderSectionHeader={sectionHeader}
        ListHeaderComponent={listHeader}
      />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff"
  },
  divider: {
    width: "100%",
    height: 2,
    backgroundColor: "#eee"
  },
  sectionHeader: {
    backgroundColor: "#5f27cd",
    paddingHorizontal: 16,
    paddingVertical: 12
  },
  sectionHeaderText: {
    fontWeight: "700",
    color: "white"
  },
  listHeader: {
    backgroundColor: "#ccc",
    paddingVertical: 32,
    paddingHorizontal: 20,
    justifyContent: "center",
    alignItems: "center"
  },
  listHeaderText: {
    fontSize: 24,
    fontWeight: "600"
  },
  singleItem: {
    paddingHorizontal: 16,
    paddingVertical: 20
  }
});

export default ScheduleScreen;
```

# Conference app: Navigation

Navigating on the web consists of a concept we can call the "history stack". When you navigate to a new place it pushes an item to the stack. Pressing the back button pops an item from the stack. This is how navigation history is maintained. A web browser tab will consist of only one stack.

Mobile navigation is a little different. An app can have multiple navigation groups and types. We'll chat more about this shortly.

The most commonly used library for navigation is `react-navigation`.

To install `react-navigation` into our project, run the following command in terminal:

``` Bash
yarn add react-navigation
```

The `react-navigation` library depends on a number of additional libraries. Install expo-supported versions of these libraries by running the following.

``` Bash
expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context
```

## Navigator types

### Stack Navigator

Provides a way for your app to transition between screens where each new screen is placed on top of the stack.

### Drawer Navigator

Creates a drawer that you can toggle in and out.

### Bottom Tab Navigator

Creates a series of tabs to allow navigating between various screens.

The stack navigator is the most common way to navigate between screens. Let's add the necessary libraries to create a stack navigator.

``` Bash
expo install react-navigation-stack @react-native-community/masked-view
```

Before moving forward, restart Expo to pickup these newly available libraries with `control + c` and `expo start`.

Back in `App.js` , import `createAppContainer` from `react-navigation` and `createStackNavigator` from `react-navigation-stack`.

`createAppContainer` sets up your app with a navigator that is passed in as a parameter. We'll need to create a navigator, then use it as a parameter for `createAppContainer`.

## Creating a navigator

Create a stack navigator using `createStackNavigator`. `createStackNavigator` takes a *route configuration object* that defines the routes in the navigator. It also supports an options object that we'll omit for now.

``` JavaScript
const AppNavigator = createStackNavigator(
  {
    Home: HomeScreen,
  }
);
```

The casing of the route name doesn't matter -- you can use lowercase home or capitalized Home, it's up to you. We prefer capitalizing our route names.

The default export in `App.js` is currently `App`. The default export needs to be the result of `createAppContainer` instead. The `App()` function and its styles can be commented out or deleted.

``` JavaScript
const AppNavigator = createStackNavigator(
  {
    Home: HomeScreen,
  }
);

export default createAppContainer(AppNavigator);
```

Run this code. You'll now see a screen with a navigation bar and a content area that displays our `HomeScreen` component! The styles you see for the navigation bar are the default configuration for a stack navigator, we'll learn how to configure and adjust those later.

Let's add additional routes for our `ScheduleScreen` and `DetailsScreen`.

``` JavaScript
const AppNavigator = createStackNavigator(
  {
    Home: HomeScreen,
    Schedule: ScheduleScreen,
    Details: DetailsScreen
  }
);
```

Running this code shows no changes. You might be asking yourself: "How does the navigator know to start from the `HomeScreen`?". Well, the first item provided in the route configuration object is always set as the starting screen unless you explicitly state the initial route in the optional options object. Play around with this to validate.

``` JavaScript
const AppNavigator = createStackNavigator(
  {
    Home: HomeScreen,
    Schedule: ScheduleScreen,
    Details: DetailsScreen
  },
  {
    initialRouteName: "Home"
  }
);
```

## Moving between screens

The next obvious question is: "How do I go from one route to another?".

The steps we took previously now provides a `navigation` property to every route component; in our case that's `HomeScreen`, `ScheduleScreen` and `DetailsScreen`.

The `HomeScreen` component currently does not use any data from passed in props. We now want to utilize the `navigation` prop. First, lets expect `props` to be passed in to the `HomeScreen` component. Use `console.log()` to verify what `props` is.

``` JavaScript
const HomeScreen = (props) => {
..
```

`navigate` is an available function on the `props.navigation` object. We can cal this with the name of the route that we'd like to move the user to.

Update the `TouchableOpacity` button to include the `onPress` prop and pass in an anonymous function which navigates the user to the "Schedule" screen.

``` JavaScript
// Step 1: add `onPress` prop

<TouchableOpacity
  style={styles.button}
  onPress={}
>

// Step 2: pass in anonymous function to onPress prop

<TouchableOpacity
  style={styles.button}
  onPress={() => {}}
>

// Step 3: use navigate function

<TouchableOpacity
  style={styles.button}
  onPress={() => {
    props.navigation.navigate("Schedule");
  }}
>
```

## Navigating to the Details Screen

Navigating from the `ScheduleScreen` to the `DetailsScreen`  will require some adjustments. First, update the `ScheduleScreen` component to accomodate props.

``` JavaScript
    const ScheduleScreen = props => {
```

Next, update the `singleItem` component to use `TouchableOpacity` since we want to navigate on press. Remember to import `TouchableOpacity` from `react-native`.


``` JavaScript
const singleItem = data => {
  const item = data.item;

  return (
    <TouchableOpacity onPress={() => {}}>
      <View style={styles.singleItem}>
        <Text>{item.title}</Text>
      </View>
    </TouchableOpacity>
  );
};
```

The `onPress` prop's function will need to call the `navigate` function on the `navigation` object, but there is a problem with our current setup. The `navigation` object is only available in the `ScheduleScreen` component's props, but we need access to it in the `singleItem` component's scope.

The simplest solution here is to move `singleItem` into the `ScheduleScreen` function before the `return`. `singleItem` now has access to `ScheduleScreen`'s scope. There is a small performance penalty for doing it this way, but its negligible for our needs and time constraint.

Update the `onPress` callback now to navigate to the "Details" screen.


``` JavaScript
const ScheduleScreen = props => {
  const singleItem = data => {
    const item = data.item;

    return (
      <TouchableOpacity onPress={() => props.navigation.navigate("Details")}>
        <View style={styles.singleItem}>
          <Text>{item.title}</Text>
        </View>
      </TouchableOpacity>
    );
  };

  return ( .. )
}
```

Navigation between all three screens is complete!

# Dynamic Details Screen

Even though navigation between the `ScheduleScreen` and the `DetailsScreen` exists, one major problem persists. The `DetailsScreen` shows hard-coded dummy data. To address this, first head to the `singleItem` function in `ScheduleScreen.js`.

The `TouchableOpacity` `onPress` prop allows us to navigate to the "Details" screen. The `navigate` function accepts a second, optional, parameter to pass data from one screen to another. Pass in the `item` as `talkData` in this optional parameter.

``` JavaScript
<TouchableOpacity
  onPress={() => props.navigation.navigate("Details", { talkData: item })}
>
```

Now in `DetailsScreen.js`, first update `DetailsScreen` to expect `props`. Optional data passed into `navigate` is available under `navigation.state.params`. Pull this object out into a variable for easy reference.

``` JavaScript
const DetailScreen = props => {
  const talkData = props.navigation.state.params.talkData;

  ..
```

Update the title, time, and description values with values from `talkData`.

``` JavaScript
<Text style={styles.title}>{talkData.title}</Text>
<Text style={styles.time}>{talkData.time}</Text>
<Text style={styles.description}>{talkData.description}</Text>
```

The speaker section is a little trickier since not every talk has a speaker (breakfast and lunch breaks). The `speaker` value in those scenarios is `null`, which we can check for and render speaker data conditionally.

``` JavaScript
{talkData.speaker && (
  <View style={styles.speaker}>
    <Image
      style={styles.avatar}
      source={{ uri: "https://i.picsum.photos/id/365/80/80.jpg" }}
    />
    <View>
      <Text style={styles.speakerName}>Speaker name</Text>
      <Text style={styles.speakerRole}>Job title</Text>
    </View>
  </View>
)}
```

And finally, update the speaker values. The final code for the `DetailsScreen` should look like the following:

``` JavaScript
const DetailsScreen = props => {
  const talkData = props.navigation.state.params.talkData;

  return (
    <View style={styles.container}>
      <View style={styles.talkDetails}>
        <Text style={styles.title}>{talkData.title}</Text>
        <Text style={styles.time}>{talkData.time}</Text>
        <Text style={styles.description}>{talkData.description}</Text>
      </View>
      {talkData.speaker && (
        <View style={styles.speaker}>
          <Image
            style={styles.avatar}
            source={{ uri: talkData.speaker.avatar }}
          />
          <View>
            <Text style={styles.speakerName}>{talkData.speaker.name}</Text>
            <Text style={styles.speakerRole}>{talkData.speaker.role}</Text>
          </View>
        </View>
      )}
    </View>
  );
};
```

# Navigation polish

The Stack Navigator creates the header on every screen in the stack. A navigation options object exists for every screen in the stack where modifications and overrides can be provided on a screen-by-screen basis.

The `title` key enables changing the header title.

``` JavaScript
HomeScreen.navigationOptions = () => ({
  title: "Derppp"
});
```

## Home Screen

The "Home" screen doesn't really need the header, so let's completely hide it by using the `headerShown` flag.

``` JavaScript
HomeScreen.navigationOptions = () => ({
  headerShown: false
});
```

## Schedule Screen

The "Schedule" screen shows the back button to navigate back to the Home screen. This isn't necessary. Hide the left header controls passing the `headerLeft` key a function that returns `null`. This doesn't completely fix the issue since you can still swipe left or tap the android back button to navigate back. The `gestureEnabled` key takes care of this.

``` JavaScript
ScheduleScreen.navigationOptions = () => ({
  headerLeft: () => null,
  gestureEnabled: false,
});
```

# All done!

And that's a wrap! You now have a fully functioning React Native app with navigation and a super cool SectionList. What we've covered today are important fundamentals that you'll need to continue your React Native adventure.

I aim to create and offer future workshops that cover intermediate and advanced concepts (data handling, state management, etc). If you're interested, do let me know and keep an eye on the #react-native Slack channel.

I'll be sending a tiny survey out after this to collect your feedback. It helps refine these workshops to make them more efficient and useful for you all.

Once again, thanks! <3
