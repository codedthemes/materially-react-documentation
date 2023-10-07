# Template Config



{% hint style="info" %}
You can edit this file at **`[ ../src/config.js ]`**
{% endhint %}

| **Option**      | **Default** | **Data Type** | **Description**                                                                                                              |
| --------------- | ----------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **gridSpacing** | 3           | number        | set grid spacing                                                                                                             |
| **drawerWidth** | 280         | number        | set drawer width                                                                                                             |
| **basename**    | /           | String        | `build time set subdomain or path of project directory`                                                                      |
| **theme**       | light       | String        | `light, dark, nav-dark`                                                                                                      |
| **rtlLayout**   | false       | boolean       | `false, true`                                                                                                                |
| **i18n**        | en          | String        | <p><code>en</code> - English</p><p><code>fr</code> - français</p><p><code>ro</code> - Română</p><p><code>zh</code> - 中国人</p> |

{% tabs %}
{% tab title="config.js" %}
```javascript

export const gridSpacing = gridSpacing ;
export const drawerWidth = drawerWidth ;

// ==============================|| THEME CONFIG  ||============================== //

const config = {
  /**
   * the props used for set home path in sub domain
   * only at build time to set
   * like, /materially/react/default
   */
  basename: 'demos/admin-templates/materially/react/stage',

  /**
   * the props used for default theme palette mode
   * explore the default theme
   * below theme options -
   * 'light' (default)
   * 'dark'
   */
  theme: 'light',

  /**
   * the props used for default theme direction
   * explore the default theme
   * below theme options -
   * 'false' (default)
   * 'true'
   */
  rtlLayout: false,

  /**
   * The props used for display menu-items with multi-language.
   * We provide static below languages according to 'react-intl' options - https://www.npmjs.com/package/react-intl
   * 'en' (default)
   * 'fr'
   * 'ro'
   * 'zh'
   */
  i18n: 'en'
};

export default config;

```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title=".env" %}
```

REACT_APP_VERSION = Version of app
...
...
```
{% endtab %}
{% endtabs %}
