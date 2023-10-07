---
description: Localization
---

# Localization

Materially supports four types of international languages ('**en**' - English, '**fr**' - French, '**ro**' - Romanian, '**zh**' - Chinese). You can switch language from the header bar. We internationalize the main menu for all four languages, When you change it from the header, you will see the effect there. If you want to configure one more language or set a default language then continue reading below...

## IntlProvider

React Intl uses the provider pattern to scope an i18n context to a tree of components. This allows configurations like the current locale and set of translated strings/messages to be provided at the root of a component tree and made available to the `<Formatted*>` components.&#x20;

## locale, formats, and messages

&#x20;The user's current locale and what the app should be rendered in. While `defaultLocale` and `defaultFormats` are for fallbacks or during development and represent the app's default. Notice how there is no, `defaultMessages`that's because each [Message Descriptor](https://formatjs.io/docs/react-intl/components#message-descriptor) provides a `defaultMessage`

## How does it work?

1.  Add node modules `react-intl` emo

    ```
    yarn add react-intl / npm install --save react-intl
    ```
2.  Data for locale files exist at **`src\utils\locales`**

    ```
    {
      "dashboard": "Dashboard",
      "default": "Default",

      "widget": "Widget",
      "widgets": "Widgets",
      "statistic": "Statistic",
    ...
    ... 
    }

    ```
3.  Open the file `config.js` and set the language.

    ```
    export default {
        ...
        i18n: 'en' // 'en' - English, 'fr' - French, 'ro' - Romanian, 'zh' - Chinese
        ...
    }
    ```
4.  Open file `App.js` and apply **IntlProvider**

    ```
    import { IntlProvider } from 'react-intl';

    function loadLocaleData(locale) {
      switch (locale) {
        case 'fr':
          return import('utils/locales/fr.json');
        case 'ro':
          return import('utils/locales/ro.json');
        case 'zh':
          return import('utils/locales/zh.json');
        default:
          return import('utils/locales/en.json');
      }
    }

    const App = () => {
        const customization = useSelector((state) => state.customization);
        const [messages, setMessages] = useState();

        useEffect(() => {
            loadLocaleData(customization.locale).then(d=>{
                setMessages(d.default);
            });
        }, [customization]);

        return (
            <React.Fragment>
            { messages && <IntlProvider
                locale='fr'
                defaultLocale="en"
                messages={messages}
                >
                ...
                ...
                ...
            </IntlProvider> }
            </React.Fragment>
        );
    };

    export default App;

    ```



