---
layout: post
title:  "Hack Edge Copilot"
date:   2024-02-3
categories: Hackathon
---

# Hack Edge Copilot

eventhough I can't scccessfully connect to wss socket, to initiate chat in postman, here is what I learn

## edge truncate service
    
    https://edgeservices.bing.com/edgesvc/postaj/sydneytruncationswithcontext?SID=####################

## bing conversation is in Chathub wss socket

    wss://sydney.bing.com/sydney/ChatHub?sec_access_token=encodeURIComponent(EncrtypedConversationSignature)

## EncrtypedConversationSignature is in url: 
https://edgeservices.bing.com/edgesvc/turing/conversation/create?bundleVersion=1.1553.1

    X-Sydney-EncryptedConversationSignature

## Interesting Setting
prompt is **Generate video highlights**
```json
"message": {
                "inputMethod": "Keyboard",
                "text": "Generate video highlights",
                "messageType": "CurrentWebpageContextRequest",
            },
            "tone": "Precise",
            "spokenTextMode": "None",
            "conversationId": "51D|EdgeCopilot|#####################",
            "previousMessages": [
                {
                    "author": "user",
                    "description": "YouTube [00:00:00] who is this Taylor Swift where in the [00:00:02] world is this this is New York City [00:00:05].......FULL YouTube Transcription",
                    "contextType": "WebPage",
                    "messageType": "Context",
                    "sourceName": "YouTube",
                    "sourceUrl": "https://www.youtube.com/watch?v=######",
                    "locale": ""
                }
            ],
```
for PDF Files

```json
"message": {
    "text": "Generate document summary, (part 1 only)",
    "messageType": "CurrentWebpageContextRequest",
    "requestId": "33b75510-f8e9-3f1f-5850-29ff2dc40f88",
    "messageId": "33b75510-f8e9-3f1f-5850-29ff2dc40f88",
    "privacy": "Internal"
}
```


## Very Interesting Observation on the wss message send to the server:

```json
{
    "arguments": [
        {
            "source": "cib",
            "optionsSets": [
                "nlu_direct_response_filter",
                "deepleo",
                "disable_emoji_spoken_text",
                "responsible_ai_policy_235",
                "enablemm",
                "dv3sugg",
                "autosave",
                "iyxapbing",
                "iycapbing",
                "enable_user_consent",
                "fluxmemcst",
                "h3imaginative",
                "enflst",
                "enpcktrk",
                "rcaldictans",
                "rcaltimeans",
                "gptvnodesc",
                "egctxtabs",
                "limitldocsum",
                "flxegvdv3"
            ],
            "allowedMessageTypes": [
                "ActionRequest",
                "Chat",
                "ConfirmationCard",
                "Context",
                "InternalSearchQuery",
                "InternalSearchResult",
                "Disengaged",
                "InternalLoaderMessage",
                "Progress",
                "RenderCardRequest",
                "RenderContentRequest",
                "AdsQuery",
                "SemanticSerp",
                "GenerateContentQuery",
                "SearchQuery",
                "GeneratedCode"
            ],
            "sliceIds": [
                "newzi",
                "ntbkf4",
                "abv2cl",
                "bcentbk",
                "mobntbk",
                "ntbk",
                "inlineadsv2",
                "inlineadscont",
                "v6voicecf",
                "291encacheas0",
                "cmcallcf",
                "kcremovedotcf",
                "tts5cf",
                "abv2mob",
                "abv2",
                "dictlog",
                "srdicton",
                "designer2tf",
                "translrefctrl",
                "0212boptpsc",
                "130memrevs0",
                "116langwbs0",
                "124multi2ts0",
                "119wcphi",
                "0131dv1",
                "enter4nl",
                "cacfastapis"
            ],
            "verbosity": "verbose",
            "scenario": "Underside",
            "plugins": [],
            "traceId": "1234567890",
            "conversationHistoryOptionsSets": [
                "autosave",
                "savemem",
                "uprofupd",
                "uprofgen"
            ],
            "isStartOfSession": false,
            "requestId": "abcdefg-6497-xyz",
            "message": {
                "locale": "en-US",
                "market": "en-US",
                "region": "US",
                "location": "lat:####;long:####;re=1000m;",
                "locationHints": [
                    {
                        "SourceType": 1,
                        "RegionType": 2,
                        "Center": {
                            "Latitude": ####,
                            "Longitude": ####
                        },
                        "Radius": 24902,
                        "Name": "Jersey City, New Jersey",
                        "Accuracy": 24902,
                        "FDConfidence": 0,
                        "CountryName": "United States",
                        "CountryConfidence": 9,
                        "Admin1Name": "New Jersey",
                        "PopulatedPlaceName": "Jersey City",
                        "PopulatedPlaceConfidence": 0,
                        "PostCodeName": "#####",
                        "UtcOffset": -5,
                        "Dma": 501
                    }
                ],
                "userIpAddress": "1.1.1.1",
                "timestamp": "2024-02-04T15:16:58-05:00",
                "author": "user",
                "inputMethod": "Keyboard",
                "text": "in this video, what else does it say",
                "messageType": "CurrentWebpageContextRequest",
                "requestId": "abcdefg-6497-xyz",
                "messageId": "abcdefg-6497-xyz"
            },
            "tone": "Precise",
            "spokenTextMode": "None",
            "conversationId": "51D|EdgeCopilot|laksdfjalksdjflaksdjflkasdjfla",
            "participant": {
                "id": "09877665544"
            }
        }
    ],
    "invocationId": "7",
    "target": "chat",
    "type": 4
}