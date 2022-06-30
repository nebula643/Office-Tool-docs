# Office Tool Plus Documentation

Office Tool Plus repository: [Office Tool](https://github.com/YerongAI/Office-Tool)

## Help with translation

``` batch
git clone https://github.com/YerongAI/Office-Tool-docs.git

cd Office-Tool-docs

yarn install

# Init local website.
yarn docs:dev
```

## How to translate?

Make a folder and named to your culture, like `de-de`.

**In the docs folder**, copy `activate`, `deploy`, `others` and `start` folders to the new folder, copy `README.md` too.

Then translate all the .md files to your language.

### Configure components

For more information, see [Internationalization](https://vuepress.vuejs.org/guide/i18n.html#site-level-i18n-config).

Go to docs -> .vuepress folder, open config.js, configure `locales` like that:

``` js
// The key is the path for the locale to be nested under.
'/de-de/': {
    lang: 'de-DE', // this will be set as the lang attribute on <html>
    title: 'Office Tool Plus Docs', // Translate it.
    description: 'Office Tool Plus documentation.' // Translate it.
}
```

Change `themeConfig -> locales` like that:

``` js
'/de-de/': {
    selectText: 'Languages', // Translate it.
    label: 'English', // Set to your language.
    editLinkText: 'Edit this page on GitHub', // Translate it.
    serviceWorker: {
        updatePopup: {
            message: "New content is available.", // Translate it.
            buttonText: "Refresh" // Translate it.
        }
    },
    nav: [
        // Remember to set the culture (ll-cc), and translate the text attributes.
        { text: 'Start', link: '/de-de/start/' },
        { text: 'Deploy', link: '/de-de/deploy/' },
        { text: 'Activate', link: '/de-de/activate/' },
        { text: 'More', link: '/de-de/others/toolbox' },
        { text: 'Blog (Chinese)', link: 'https://www.coolhub.top' },
        {
            text: 'Group', items: [
                { text: 'Telegram', link: 'https://otp.landian.vip/grouplink/telegram.html' }
            ]
        }
    ],
    sidebar: {
        // Remember to set the culture (ll-cc).
        '/de-de/start/': [
            '',
            'download',
            'requirement'
        ],
        '/de-de/deploy/': [
            '',
            'deploy',
            'create-iso',
            'faq'
        ],
        '/de-de/activate/': [
            '',
            'faq'
        ],
        '/de-de/others/': [
            'toolbox',
            'converter',
            ''
        ],
        '/de-de/': [
            ''
        ]
    }
},
```
