# FINCH DELIVERY APP

## SET UP
1. Open CMD or Windows Powershell and write the commands:
    ```shell
        npx create-expo-app finch-delivery-app
        cd finch-delivery-app
        code .
    ```
1. VSCode will appear, open the terminal:
    ```shell
        expo start
    ```
1. Install [Tailwind CSS](https://www.nativewind.dev/quick-starts/react-native-cli) and restart project due to changes in Babel.
    ```shell
        npm install nativewind
        npm install --dev tailwindcss

        # Initialize tailwind.config.js
        npx tailwindcss init

        # tailwind.config.js
        /** @type {import('tailwindcss').Config} */
        module.exports = {
        content: ["./App.{js,jsx,ts,tsx}", 
        "./pages/**/*.{js,jsx,ts,tsx}",
        ],
        theme: {
            extend: {},
        },
        plugins: [],
        }

        # babel.config.js
        module.exports = function(api) {
        api.cache(true);
        return {
            presets: ['babel-preset-expo'],
            plugins: ["nativewind/babel"],
        };
        };
    ```
1. Install [React Navigation](https://reactnavigation.org/docs/getting-started/)
    ```shell
        npm install @react-navigation/native

        npx expo install react-native-screens react-native-safe-area-context

        npm install @react-navigation/native-stack

        #App.js
        import { NavigationContainer } from '@react-navigation/native';
        import { createNativeStackNavigator } from '@react-navigation/native-stack';
        import HomeScreen from './screens/HomeScreen';

        const Stack = createNativeStackNavigator();

        export default function App() {
        return (
            <NavigationContainer>
                <Stack.Navigator>
                    <Stack.Screen name="Home" component={HomeScreen} />
                </Stack.Navigator>
            </NavigationContainer>
        );
        }

    ```

1. Install [React Native Heroicons](https://www.npmjs.com/package/react-native-heroicons)
    ```shell
        npm i react-native-heroicons react-native-svg
    ```
    - **NOTE:** This will create an error: `Invariant Violation: requireNativeComponent: "RNSVGSvgViewAndroid" was not found in the UIManager.` because Android is only compatible with `"react-native-svg": "13.4.0` but this will install version 13.6.0. To solve that, run in the terminal:
    ```shell
        npx expo install react-native-svg
    ```
    