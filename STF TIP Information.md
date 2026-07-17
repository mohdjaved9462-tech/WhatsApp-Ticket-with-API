# **STF TIP Information**



{

&nbsp; "nodes": \[

&nbsp;   {

&nbsp;     "parameters": {

&nbsp;       "public": true,

&nbsp;       "initialMessages": "Hi there! 👋\\nMy name is Javed. How can I assist you today?",

&nbsp;       "options": {}

&nbsp;     },

&nbsp;     "type": "@n8n/n8n-nodes-langchain.chatTrigger",

&nbsp;     "typeVersion": 1.4,

&nbsp;     "position": \[

&nbsp;       -880,

&nbsp;       -384

&nbsp;     ],

&nbsp;     "id": "f9a89174-6c23-4aae-b2c9-2b96dfcb8187",

&nbsp;     "name": "When chat message received",

&nbsp;     "webhookId": "c3ac0ef2-b5a4-48f6-bb97-6349956649de"

&nbsp;   },

&nbsp;   {

&nbsp;     "parameters": {

&nbsp;       "documentId": {

&nbsp;         "\_\_rl": true,

&nbsp;         "value": "https://docs.google.com/spreadsheets/d/1E3z5p7-NSCsWXorP6ZcPZCzhiHlRaK7Kuy9mYhzd7Sw/edit?invite=COqQlp8L\&gid=1363514854#gid=1363514854",

&nbsp;         "mode": "url"

&nbsp;       },

&nbsp;       "sheetName": {

&nbsp;         "\_\_rl": true,

&nbsp;         "value": "Form responses 1",

&nbsp;         "mode": "name"

&nbsp;       },

&nbsp;       "options": {}

&nbsp;     },

&nbsp;     "type": "n8n-nodes-base.googleSheets",

&nbsp;     "typeVersion": 4.7,

&nbsp;     "position": \[

&nbsp;       -656,

&nbsp;       -384

&nbsp;     ],

&nbsp;     "id": "0f5ba33e-8eac-464a-ba42-885832434292",

&nbsp;     "name": "Get row(s) in sheet",

&nbsp;     "credentials": {

&nbsp;       "googleSheetsOAuth2Api": {

&nbsp;         "id": "oHTFnaXwNsKn76e9",

&nbsp;         "name": "Google Sheets account 2"

&nbsp;       }

&nbsp;     }

&nbsp;   },

&nbsp;   {

&nbsp;     "parameters": {

&nbsp;       "jsCode": "// 🔹 Final result array\\nconst results = \[];\\n\\n// 🔹 Loop through ALL rows\\nfor (const item of items) {\\n  const row = item.json;\\n\\n  // 🔹 Helper for complex / multiline headers\\n  function getByIncludes(keyword) {\\n    const key = Object.keys(row).find(k =>\\n      k.replace(/\\\\s+/g, \\" \\").includes(keyword)\\n    );\\n    return key ? row\[key] : \\"\\";\\n  }\\n\\n  // 🔹 Push structured data for each row\\n  results.push({\\n    RowNumber: row.row\_number,\\n    TipDate: row\[\\"Column 1\\"],\\n\\n    ReporterEmailAddress: row\[\\"Email address\\"],\\n    ReporterName: row\[\\"NAME (नाम)\\"],\\n    ReporterFatherName: row\[\\"Father’s Name ( पिता का नाम)\\"],\\n    ReporterAddress: row\[\\"Address (पता)\\"],\\n    ReporterMobileNumber: row\[\\"Mobile Number ( मोबाइल नंबर)\\"],\\n    ReporterEmailId: row\[\\"Email ID ( ईमेल आईडी)\\"],\\n\\n    CrimeCategory: getByIncludes(\\"II. CATEGORY OF CRIME\\"),\\n    SpecificAddress: row\[\\"Specific Address (सटीक पता)\\"],\\n    CityTownVillage: row\[\\"City शहर/Town कस्बा/Village गांव\\"],\\n    State: row\[\\"State (राज्य)\\"],\\n    District: row\[\\"District (जिला)\\"],\\n    PinCode: row\[\\"Pin Code पिनकोड (if known/यदि ज्ञात हो)\\"],\\n\\n    SuspectName: row\[\\"Name (नाम)\\"],\\n    SuspectFatherName: row\[\\"Father's Name (पिता का नाम)\\"],\\n    SuspectMotherName: row\[\\"Mother's Name (माता का नाम)\\"],\\n    SuspectAliasOrNickname: row\[\\"Alias/Nickname उपनाम (if any/यदि कोई हो)\\"],\\n    \\n    SuspectPhoneNumber: row\[\\"Phone Number (फोननंबर)\\"],\\n    SuspectPersonalIdNumbers: row\[\\"Personal ID Numbers पहचानसंख्या (if any/यदिकोईहो)\\"],\\n    SuspectResidentialAddress: row\[\\"Residential Address (निवास पता)\\"],\\n\\n    GangAffiliation: row\[\\"Gang Affiliation (गैंग का नाम)\\"],\\n    WhatsAppNumber: row\[\\"WhatsApp Number (व्हाट्सएप नंबर)\\"],\\n    TelegramHandle: row\[\\"Telegram Handle (टेलीग्राम हैंडल)\\"],\\n    InstagramId: row\[\\"Instagram ID (इंस्टाग्राम आईडी)\\"],\\n    FacebookId: row\[\\"Facebook ID (फेसबुक आईडी)\\"],\\n    SnapchatId: row\[\\"Snapchat ID (स्नैपचैट आईडी)\\"],\\n\\n    OtherEncryptedApps: row\[\\"Signal सिग्नल/ Zangi  ज़ैंगी/ Other Encrypted Apps अन्य एन्क्रिप्टेड ऐप्स\\"],\\n    EncryptedAppsDetails: getByIncludes(\\"Encrypted\\"),\\n    SocialMediaProfileLinks: getByIncludes(\\"Social Media Profile Links\\"),\\n\\n    ScreenshotsChatLogsPosts: getByIncludes(\\"Screenshots\\"),\\n    FinancialTransactionDetails: getByIncludes(\\"Financial Transaction Details\\"),\\n    VideoRecordingsOrCctvClips: row\[\\"Video Recordings वीडियो रिकॉर्डिंग / CCTV Clips सीसीटीवी फुटेज\\"],\\n    AudioRecordings: row\[\\"Audio Recordings  (ऑडियो रिकॉर्डिंग)\\"],\\n    ScreenshotsOfChatsPostsImages: getByIncludes(\\"Screenshots (of chats/posts/images)\\"),\\n    DocumentsOrIdProof: getByIncludes(\\"Documents/ID proof related to suspect\\"),\\n    VehicleOrPropertyDetails: row\[\\"Vehicle वाहन/Property Details संपत्ति की जानकारी\\"],\\n    OtherMaterials: row\[\\"Other Materials  अन्य सामग्री (specify/स्पष्टकरें)\\"],\\n    BriefDescription: row\[\\"(Please describe briefly what you know – Max. 500 words / कृपया संक्षेप में विवरण दें – अधिकतम 500 शब्द)\\"],\\n    Remark: row\[\\"Column 37\\"]\\n  });\\n}\\n\\n// ?? Take last 10, then remove last 2 from them\\nconst finalRecords = results.slice(-10, -2);\\n\\nreturn \[{\\n  json: {\\n    total\_records: finalRecords.length,\\n    records: finalRecords\\n  }\\n}];\\n"

&nbsp;     },

&nbsp;     "type": "n8n-nodes-base.code",

&nbsp;     "typeVersion": 2,

&nbsp;     "position": \[

&nbsp;       -416,

&nbsp;       -384

&nbsp;     ],

&nbsp;     "id": "c2316dc0-191b-4703-84ab-f77dbc81010a",

&nbsp;     "name": "Code in JavaScript"

&nbsp;   }

&nbsp; ],

&nbsp; "connections": {

&nbsp;   "When chat message received": {

&nbsp;     "main": \[

&nbsp;       \[

&nbsp;         {

&nbsp;           "node": "Get row(s) in sheet",

&nbsp;           "type": "main",

&nbsp;           "index": 0

&nbsp;         }

&nbsp;       ]

&nbsp;     ]

&nbsp;   },

&nbsp;   "Get row(s) in sheet": {

&nbsp;     "main": \[

&nbsp;       \[

&nbsp;         {

&nbsp;           "node": "Code in JavaScript",

&nbsp;           "type": "main",

&nbsp;           "index": 0

&nbsp;         }

&nbsp;       ]

&nbsp;     ]

&nbsp;   },

&nbsp;   "Code in JavaScript": {

&nbsp;     "main": \[

&nbsp;       \[]

&nbsp;     ]

&nbsp;   }

&nbsp; },

&nbsp; "pinData": {},

&nbsp; "meta": {

&nbsp;   "templateCredsSetupCompleted": true,

&nbsp;   "instanceId": "fc8ea56a9f77461efdbaf4ab14000fda259d6eb0a0ad047cd98c8f84ded3bdb0"

&nbsp; }

}

