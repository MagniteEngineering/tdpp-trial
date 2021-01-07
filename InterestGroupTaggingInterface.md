# Interest Group Tagging Interface

We will implement an interface for tagging users into an interest group and providing ads/bids

A JS function will be exposed:

```javascript
TDTest.writeAdvertisementData(input);
```

Which takes an object as input with the following structure:

```javvascript
{
    'advertiser': 'https://advertiser.example',
    'dsp': 'https://dsp.example',
    'ssps': [
        'https://ssp-1.example',
        'https://ssp-2.example'
    ],
    'groups': {
        'interest-group-1': {
            'timestamp': ts,
            'ttl': duration
        },
        'interest-group-2': {
            'timestamp': ts,
            'ttl': duration
        }
    },
    'decision-logic-url': 'https://dsp.example/js/bidding.js',
    'ads': [
        {
            'name': 'ad-123456789',
            'formats': [
                {
                    'aspect_ratio': '16:9',
                    'min_height': 400,
                    'max_height': 800
                }
            ],
            'ad-cbor-url': 'https://dsp.example/ads/ad-123456789.wbn',
            'dsp-categories': [
                'cat1',
                'cat2',
                'cat3'
            ],
            'cache-lifetime-secs': 21600,
            'privateData': { ... }
        },
        {
            'name': 'ad-987654321',
            'formats': ['1024x768', '512x384'],
            'ad-cbor-url': 'https://dsp.example/ads/ad-987654321.wbn',
            'dsp-categories': ['cat4', 'cat5'],
            'cache-lifetime-secs': 86400,
            'max-times-per-minute': 1,
            'max-times-per-hour': 12,
            'privateData': { ... }
        }
    ]
}
```

| Parameter                | Description                                                                                                          | Type                           | Source | Sample Value                                                                     |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------- | ------------------------------ | ------ | -------------------------------------------------------------------------------- | --- | ----------------------- |
| advertiser               | Advertiser determining interest groups.                                                                              | Domain                         |        | https://advertiser.example                                                       |
| dsp                      | DSP who is responsible for setting interest group                                                                    | Domain                         |        | https://dsp.example                                                              |
| ssps                     |                                                                                                                      | Array[Domain]                  |        |                                                                                  |
| groups                   | Interest Groups                                                                                                      | Array[Object]                  |        |                                                                                  |
| third-parties            | Auction observers who should also have access to some reporting info                                                 | Object { domain: reportingUrl} |        | {'https://third-party-1.example': 'https://third-party-1.example/js/metrics.js'} |
| decision-logic-url       | Url of js function which can be used to produce a bid using auction time information                                 | Url of javascript function     |        | https://dsp.example/js/bidding.js                                                |
| ads                      |                                                                                                                      | Array[Object]                  |        |                                                                                  |
| ads.name                 | Name or ID of the ad. Must be unique within the advertiser                                                           | String                         |        | ad-987654321'                                                                    |
| ads.formats              | Array of formats. Can be an array of standard format strings, or objects containing aspect ratio and min/max height. | Array[enum                     |        | Object]                                                                          |     | ['1024x768', '512x384'] |
| ads.formats.aspect_ratio | Aspect ratio of the format                                                                                           | String [width]:[height]        |        | 16:9'                                                                            |
| ads.format.min_height    | Minimum height of the ad                                                                                             | Int                            |        | 300                                                                              |
| ads.format.max_height    | Maximum height of the ad                                                                                             | Int                            |        | 400                                                                              |
| ads.ad-cbor-url          | Url of the creative bundle                                                                                           | String                         |        | https://dsp.example/ads/ad-987654321.wbn                                         |
| ads.dsp-categories       | Ad category used by the DSP                                                                                          | Array(String)                  |        | ['cat4', 'cat5']                                                                 |
| ads.cache-lifetime-secs  | How long the given ad is valid                                                                                       | Int                            |        | 86400                                                                            |
| ads.max-times-per-minute | Frequency the ad can show to the user each minute                                                                    | int                            |        | 1                                                                                |
| ads.max-times-per-hour   | Frequency the ad can show to the user each hour                                                                      | int                            |        | 12                                                                               |
| ads.privateData          | Object which can be used to extend features beyond the spec                                                          | Object                         |        | { foo: bar }                                                                     |
