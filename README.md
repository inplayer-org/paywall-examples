# InPlayer Paywall

[inplayer.com](https://inplayer.com)

#### Paywall v3 Staging url: https://event.inplayer.com/v3/staging/?asset=49074

#### Paywall v3 Sandbox url: https://event.inplayer.com/v3/sandbox?asset=49074

#### Paywall v3 Live url: https://event.inplayer.com/v3/live?asset=39084

## Installation

Install the package from [npm](https://www.npmjs.com/package/@inplayer-org/paywall) and import it in your project.

```bash
npm install --save @inplayer-org/paywall
```

Alternately include the script like so:

```
<script src="https://assets.inplayer.com/paywall/0.1.0/paywall.min.js"></script>
```

## Loading an asset with ID

#### Example:

```
// Basic example  InPlayerPaywall(merchantUUID, [Object{id, ...options}])
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112,
        options: {
          preselectedFeeId: 4410, // optional, a price option to be selected by default and effectively skip the Price Options screen
          noInject: true, // optional
          noPreview: false, // optional
          brandingId: "597", // optional
          showPreviewPrices: true, // optional
          registerFirst: true, // optional, false by default, if true it sets the Register screen as default, as opposed to the Login screen
        }
      }
    ]
  );
</script>
```

## Loading an asset with external ID

#### Example:

```
<div id="inplayer-brightcove-5784466086001" class="inplayer-paywall" />
<script>
  // This id is an external one, the type has to be specified as well.
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        external: {
          type: 'brightcove',
          id: 5784466086001,
        },
        options: {
          preselectedFeeId: 4410, // optional, a price option to be selected by default and effectively skip the Price Options screen
          noInject: true, // optional, false by default, if true the asset content will not be injected
          noPreview: false, // optional
          brandingId: "597", // optional
          showPreviewPrices: true, // optional
          registerFirst: true, // optional
        }
      },
    ]
  );
</script>
```

## Loading an asset in a custom container

#### Example:

```
// Basic example  InPlayerPaywall(merchantUUID, [Object{id, ...options}])
<div id="custom-asset-container" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112,
        containerId: 'custom-asset-container', // optional, for using a custom asset container as opposed to the default 'inplayer-40112'
        options: {
          noPreview: false,
          brandingId: "597",
        }
      }
    ]
  );
</script>
```

## Main available ASSET options

- noPreview
- brandingId
- showPreviewPrices
- enableDarkMode

#### Example:

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  // No preview option, branding option and show prices preview option
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112,
        options: {
          noPreview: true, // false by default - the preview won't show if enabled
          brandingId: "51424", // Enables usage of branding different than the default one
          showPreviewPrices: true, // false by default - the prices preview will be shown in the preview if enabled
          enableDarkMode: true // false by default
        }
      }
    ]
  );
</script>
```

## Additional Paywall options

- default paywall language
- show/hide the user menu
- show/hide the logo in the modal

#### Example:

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  // InplayerPaywall(merchant UUID, [Object{id, ...opts}], {...opts})
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112
      },
    ],
    {
      language: 'de', // sets the fallback language, 'en' by default
      hideUserMenu: true, // false by default, hides the user menu dropdown (false by default)
      hideLogo: true, // false by default, hides the logo in the modal header (false by default)
      registerFirst: true, // optional, false by default, if true it sets the Register screen as default, as opposed to the Login screen
    }
  );
</script>

// Hide or customise the footer links
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  // InplayerPaywall(merchant UUID, [Object{id, ...opts}], {...opts})
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112
      },
    ],
    {
      footerLinks: [{ text: 'Custom text', url: '//some.custom.link' }], // optional, array of footer links to replace the default ones
      hideFooterLinks: true, // false by default, if true footer links will not be displayed
      hideProtectedBy: true, // false by default, if true the 'Protected by InPlayer' label will not be displayed
    }
  );
</script>

// Paywall options regarding authentication
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  // InplayerPaywall(merchantUUID, [Object{id, ...opts}], {...opts})
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112
      },
    ],
    {
      oauthAppKey: 'some-key', // optional, merchantUUID will be used by default
      ssoDomain: 'https://appkey.sso.domain.url', // optional, providing a valid SSO domain enables the SSO feature
    }
  );
</script>
```

## Standalone Paywall functions

- setLanguage
- setLoginScreen
- setRegisterScreen
- logoutUser
- showMyAccount
- showCreditCardDetails
- showChangePassword
- showPaywall

#### Example:

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
          id: 40112
      },
    ],
  );

  paywall.setLanguage('en'); // sets the active paywall language
  paywall.setLoginScreen(); // displays the paywall login screen
  paywall.setRegisterScreen(); // displays the register screen
  paywall.logoutUser(); // logs out the logged in user
  paywall.showMyAccount(); // displays the my account screen (the user needs to be authenticated)
  paywall.showCreditCardDetails(); // displays the Credit Card Details screen (the user needs to be authenticated)
  paywall.showChangePassword(); // displays the Change Password screen (the user needs to be authenticated)

  paywall.showPaywall({
    options: {
      asset: { ...asset }, // optional
    } // optional
  }); // displays the paywall (same as when you would click on the buy button)
</script>
```

## Other Paywall methods

- checkUserAccess - check if the user has access for the specified combination of assetId, clientId and accessFeeId

#### Example:

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
          id: 40112
      },
    ],
  );

 async paywall.checkUserAccess(assetId, clientId, accessFeeId);
</script>
```

## Asset manipulation methods and options

- addAssets - adds assets to the paywall instance
- removeAssets - removes specified assets from the paywall instance. IMPORTANT: They have to be specified exactly as they were added - if containerId was specified on adding, it would also have to be specified on removal
- removeAllAssets - removes all assets from the paywall instance. IMPORTANT: The paywall instance remains "alive" and other assets can be added to it at any later time
- hasAsset - returns a boolean indicating whether the paywall instance contains a specified asset (either having been added by using the `addAssets` method or when the paywall instance was created)
- destroy - destroys the paywall instance. After this the instance can no longer be used in any way
- isDestroyed - a boolean indicating whether the instance has been destroyed

#### Example:

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112
      },
    ],
  );

  paywall.addAssets([
    {
      id: 40113,
      options: {
        brandingId: 569.
      },
    },
    {
      external: {
        type: 'brightcove',
        id: '5784466086001',
      },
      containerId: 'bc-custom-asset-container-for-id-5784466086001',
      options: {
        brandingId: 564,
      },
    }
  ]);

  if (paywall.hasAsset({ id: 40113 })) {
    paywall.removeAssets([
      {
        id: 40113,
      },
      true =========================\    ______________________________________________________
    ]);                              \  / keep asset data (optional argument, false by default)
                                      \/  If true, it tells the paywall instance to keep all the data of the asset(s) it's to unmount,
                                          so the data can be reused if possibly the same assets are to be re-added (by using the .addAssets() method),
                                      /\  making the asset re-mounting a bit faster by not making some of the backend API calls all over again
    paywall.removeAllAssets(         /  \______________________________________________________
      true =========================/
    );
  }

  paywall.destroy();
  paywall.isDestroyed();
</script>
```

## Asset manipulation paywall options

-  allowRemoveAssets - true by default. If the user doesn't want to allow removal of assets at any point, they should set this option to false upon creating the paywall instance. It can't be changed later than that. Once set to false paywall.removeAssets() and paywall.removeAllAssets() will not work, but will display a non-blocking error message in the console
- allowDestroy - true by default. If the user doesn't want to allow destroying of the paywall instance at any point, they must set this options to fase upon creating the paywall instance. It can't be changed later than that. Once set to false paywall.destroy() will not work, but will display a non-blocking error message in the console

#### Example:

```
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112
      },
    ],
    {
      allowRemoveAssets: false,
      allowDestroy: false
    }
  );
</script>
```

## Additional ASSET options

- Additional CSS/JS scripts import
- Additional Query Params for asset initialization

#### Importing scripts (CSS/JS):

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112,
        options: {
          noPreview: true, // false by default - the preview wont show if enabled
          brandingId: "51424", // Enables usage of branding different than the default one
          showPreviewPrices: true, // false by default - the prices preview will be shown in the preview if enabled
          playerScripts: [
            {
              src: 'https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js',
              type: 'script',
              id: 'my-custom-id',
              async: false // optional - whether the script should be loaded async (true by default)
              parent: 'container-id' /* optional - the id of the element which should be the parent of the script, document.body by default
            },
            {
              href: 'https://ajax.googleapis.com/jquery.mobile.min.css',
              type: 'style',
              parent: 'container-id' /* optional - the id of the element which should be the parent of the css, document.head by default
            }
          ],
        }
      }
    ]
  );
</script>
```

#### Adding custom player params for the OVP (usually a video player) used by the asset:

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112,
        options: {
          noPreview: true, // false by default - the preview won't show if enabled
          brandingId: "51424", // Enables usage of branding different than the default one
          showPreviewPrices: true, // false by default - the prices preview will be shown in the preview if enabled
          playerParams: {
            language: 'en',
            myParam: 'any value'
          }
        }
      }
    ]
  );
</script>
```

####  Disable the voucher feature

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112,
        options: {
          disableVoucher: true, // false by default, if true the voucher section will not be shown
        }
      }
    ]
  );
</script>
```

#### Embed a code-access asset:

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  var paywall = new InplayerPaywall('c6f4002f-7415-4eb6-ab03-72b0f7aff0e8',
    [
      {
        id: 40112,
        options: {
          codeAccess: {
            inputs: {
              access_code: 'custom placeholder for the access_code input', // optional
              customInput1: 'This string will be the placeholder of customInput1', // this is a custom input
              customInput2: 'This string will be the placeholder of customInput2', // this is a custom input
            },
            codePattern: '{{customInput1}}-{{customInput2}}-{{access_code}}',
          }, // optional, default value is { inputs: { access_code: 'Code' }, codePattern: '{{access_code}}' }
        }
      }
    ]
  );
</script>
```

#### Demo mode feature:

```
<div id="inplayer-40112" class="inplayer-paywall" />
<script>
  const merchantUuid = 'c6f4002f-7415-4eb6-ab03-72b0f7aff0e8';

  const accountData = {
    id: 111,
    email: 'demo@inplayer-demo-mail.com',
    full_name: 'Demo Name',
    referrer: 'Inplayer Dashboard',
    metadata: {},
    social_apps_metadata: [],
    roles: [],
    completed: true,
    created_at: 123456789,
    updated_at: 123456789,
    uuid: 'uuid',
    merchant_uuid: merchantUUID,
  };

  const signIn_signUp_mockupData = {
    access_token: 'demo-mode-token',
    refresh_token: 'demo-mode-refresh-token',
    expires: '9999999999',
    account: accountData,
  };

  const commonResponse = {
    code: 404,
    message: '',
  };

  var paywall = new InplayerPaywall(merchantUuid,
    [{ id: 40112 }],
    {},
    {
      enabled: true, // false by default, true to enable demo mode
      loggedInOnStart: true, // false by default, if true it only works with enabled: true
      hasAccessOnStart: true, // false by default, if true it only works with enabled: true
      mockups: {
        Account: {
          getAccountInfo: accountData,
          signIn: signIn_signUp_mockupData,
          signUp: signIn_signUp_mockupData,
          getSocialLoginUrls: [],
          requestNewPassword: commonResponse,
          changePassword: {},
          updateAccount: accountData,
          sendPinCode: commonResponse,
          validatePinCode: commonResponse,
        },
        Payment: {
          getPaymentMethods: [
            { id: 1, method_name: 'Card', is_external: false },
          ],
          createPayment: {},
        },
        Subscription: {
          createSubscription: {},
        },
        Asset: {
          checkAccessForAsset: assetId => ({
            id: assetId,
            account_id: 1,
            customer_id: 1,
            customer_uuid: '1',
            ip_address: '1',
            country_code: 'MK',
            created_at: 123456789,
            expires_at: 123456789,
            starts_at: 123456789,
            item: {
              content: 'asset content here',
              id: assetId,
              merchant_id: 1,
              merchant_uuid: merchantUuid,
              is_active: true,
              title: 'title',
              access_control_type: {
                id: 1,
                name: 'name',
                auth: true,
              },
              item_type: {
                id: 1,
                name: 'name',
                content_type: 'html',
                description: 'description',
              },
              age_restriction: undefined,
              metadata: {},
              created_at: 123456789,
              updated_at: 123456789,
            },
          }),
        },
      },
    }
  );
</script>
```
