
## Event Categories


The following table lists the data source offered by this integration.

| Data Source | Description                          |
| ----------- | ------------------------------------ |
| `Email gateway` | Proofpoint TAP inspect, classify and detect threats targetting people through email. |





In details, the following table denotes the type of events produced by this integration.

| Name | Values |
| ---- | ------ |
| Kind | `event` |
| Category | `email`, `network` |
| Type | `info` |




## Event Samples

Find below few samples of events and how they are normalized by SEKOIA.IO.


=== "test_click_permitted.json"

    ```json
	
    {
        "@timestamp": "2016-06-24T19:17:44.000Z",
        "message": "{\"campaignId\":\"46e01b8a-c899-404d-bcd9-189bb393d1a7\",\"classification\":\"MALWARE\",\"clickIP\":\"192.0.2.1\",\"clickTime\":\"2016-06-24T19:17:44.000Z\",\"GUID\":\"b27dbea0-87d5-463b-b93c-4e8b708289ce\",\"id\":\"8c8b4895-a277-449f-r797-547e3c89b25a\",\"messageID\":\"8c6cfedd-3050-4d65-8c09-c5f65c38da81\",\"recipient\":\"bruce.wayne@pharmtech.zz\",\"sender\":\"9facbf452def2d7efc5b5c48cdb837fa@badguy.zz\",\"senderIP\":\"192.0.2.255\",\"threatID\":\"61f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50\",\"threatTime\":\"2016-06-24T19:17:46.000Z\",\"threatURL\":\"https://threatinsight.proofpoint.com/#/73aa0499-dfc8-75eb-1de8-a471b24a2e75/threat/u/61f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50\",\"threatStatus\":\"active\",\"url\":\"http://badguy.zz/\",\"userAgent\":\"Mozilla/5.0(WindowsNT6.1;WOW64;rv:27.0)Gecko/20100101Firefox/27.0\",\"type\":\"click\",\"status\":\"permitted\"}\n",
        "event": {
            "kind": "event",
            "type": [
                "allowed"
            ],
            "category": [
                "network"
            ],
            "action": "permitted",
            "dataset": "click"
        },
        "observer": {
            "vendor": "ProofPoint",
            "product": "Targeted Attack Protection"
        },
        "email": {
            "to": {
                "address": [
                    "bruce.wayne@pharmtech.zz"
                ]
            },
            "sender": {
                "address": [
                    "9facbf452def2d7efc5b5c48cdb837fa@badguy.zz"
                ]
            },
            "local_id": "b27dbea0-87d5-463b-b93c-4e8b708289ce",
            "message_id": "8c6cfedd-3050-4d65-8c09-c5f65c38da81"
        },
        "related": {
            "ip": [
                "192.0.2.255"
            ]
        },
        "source": {
            "ip": "192.0.2.255",
            "address": "192.0.2.255"
        },
        "url": {
            "original": "http://badguy.zz/",
            "domain": "badguy.zz",
            "path": "/",
            "port": 80,
            "scheme": "http",
            "subdomain": "badguy"
        },
        "user_agent": {
            "original": "Mozilla/5.0(WindowsNT6.1;WOW64;rv:27.0)Gecko/20100101Firefox/27.0"
        },
        "threat": {
            "enrichments": [
                {
                    "indicator": {
                        "first_seen": "2016-06-24T19:17:46.000Z",
                        "last_seen": "2016-06-24T19:17:46.000Z",
                        "reference": "https://threatinsight.proofpoint.com/#/73aa0499-dfc8-75eb-1de8-a471b24a2e75/threat/u/61f7622167144dba5e3ae4480eeee78b23d66f7dfed970cfc3d086cc0dabdf50",
                        "type": "domain-name",
                        "url": {
                            "original": "http://badguy.zz/"
                        }
                    }
                }
            ]
        },
        "proofpoint": {
            "tap": {
                "threat": {
                    "classifications": [
                        "malware"
                    ]
                }
            }
        }
    }
    	
	```


=== "test_message_blocked.json"

    ```json
	
    {
        "@timestamp": "2016-06-24T21:18:38.000Z",
        "message": "{\"GUID\":\"c26dbea0-80d5-463b-b93c-4e8b708219ce\",\"status\":\"delivered\",\"type\":\"message\",\"QID\":\"r2FNwRHF004109\",\"ccAddresses\":[\"bruce.wayne@university-of-education.zz\"],\"clusterId\":\"pharmtech_hosted\",\"completelyRewritten\":\"true\",\"fromAddress\":[\"badguy@evil.zz\"],\"headerCC\":\"\\\"Bruce Wayne\\\" <bruce.wayne@university-of-education.zz>\",\"headerFrom\":\"\\\"A. Badguy\\\" <badguy@evil.zz>\",\"headerReplyTo\":null,\"headerTo\":\"\\\"Clark Kent\\\" <clark.kent@pharmtech.zz>; \\\"Diana Prince\\\" <diana.prince@pharmtech.zz>\",\"impostorScore\":0,\"malwareScore\":100,\"messageID\":\"20160624211145.62086.mail@evil.zz\",\"messageParts\":[{\"contentType\":\"text/plain\",\"disposition\":\"inline\",\"filename\":\"text.txt\",\"md5\":\"008c5926ca861023c1d2a36653fd88e2\",\"oContentType\":\"text/plain\",\"sandboxStatus\":\"unsupported\",\"sha256\":\"85738f8f9a7f1b04b5329c590ebcb9e425925c6d0984089c43a022de4f19c281\"},{\"contentType\":\"application/pdf\",\"disposition\":\"attached\",\"filename\":\"Invoice for Pharmtech.pdf\",\"md5\":\"5873c7d37608e0d49bcaa6f32b6c731f\",\"oContentType\":\"application/pdf\",\"sandboxStatus\":\"threat\",\"sha256\":\"2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca\"}],\"messageTime\":\"2016-06-24T21:18:38.000Z\",\"modulesRun\":[\"pdr\",\"sandbox\",\"spam\",\"urldefense\"],\"phishScore\":46,\"policyRoutes\":[\"default_inbound\",\"executives\"],\"quarantineFolder\":\"Attachment Defense\",\"quarantineRule\":\"module.sandbox.threat\",\"recipient\":[\"clark.kent@pharmtech.zz\",\"diana.prince@pharmtech.zz\"],\"replyToAddress\":null,\"sender\":\"e99d7ed5580193f36a51f597bc2c0210@evil.zz\",\"senderIP\":\"192.0.2.255\",\"spamScore\":4,\"subject\":\"Please find a totally safe invoice attached.\",\"threatsInfoMap\":[{\"campaignId\":\"46e01b8a-c899-404d-bcd9-189bb393d1a7\",\"classification\":\"MALWARE\",\"threat\":\"2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca\",\"threatId\":\"2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca\",\"threatStatus\":\"active\",\"threatTime\":\"2016-06-24T21:18:38.000Z\",\"threatType\":\"ATTACHMENT\",\"threatUrl\":\"https://threatinsight.proofpoint.com/#/73aa0499-dfc8-75eb-1de8-a471b24a2e75/threat/u/2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca\"},{\"campaignId\":\"46e01b8a-c899-404d-bcd9-189bb393d1a7\",\"classification\":\"MALWARE\",\"threat\":\"badsite.zz\",\"threatId\":\"3ba97fc852c66a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa\",\"threatTime\":\"2016-06-24T21:18:07.000Z\",\"threatType\":\"url\",\"threatUrl\":\"https://threatinsight.proofpoint.com/#/73aa0499-dfc8-75eb-1de8-a471b24a2e75/threat/u/3ba97fc852c66a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa\"}],\"toAddresses\":[\"clark.kent@pharmtech.zz\",\"diana.prince@pharmtech.zz\"],\"xmailer\":\"Spambot v2.5\"}",
        "event": {
            "kind": "event",
            "action": "delivered",
            "type": [
                "info"
            ],
            "category": [
                "email"
            ],
            "dataset": "message"
        },
        "related": {
            "ip": [
                "192.0.2.255"
            ]
        },
        "observer": {
            "vendor": "ProofPoint",
            "product": "Targeted Attack Protection"
        },
        "email": {
            "cc": {
                "address": [
                    "bruce.wayne@university-of-education.zz"
                ]
            },
            "from": {
                "address": [
                    "badguy@evil.zz"
                ]
            },
            "to": {
                "address": [
                    "clark.kent@pharmtech.zz",
                    "diana.prince@pharmtech.zz"
                ]
            },
            "sender": {
                "address": [
                    "e99d7ed5580193f36a51f597bc2c0210@evil.zz"
                ]
            },
            "x_mailer": "Spambot v2.5",
            "subject": "Please find a totally safe invoice attached.",
            "local_id": "c26dbea0-80d5-463b-b93c-4e8b708219ce",
            "message_id": "20160624211145.62086.mail@evil.zz",
            "attachments": [
                {
                    "file": {
                        "mime_type": "text/plain",
                        "name": "text.txt",
                        "hash": {
                            "md5": "008c5926ca861023c1d2a36653fd88e2",
                            "sha256": "85738f8f9a7f1b04b5329c590ebcb9e425925c6d0984089c43a022de4f19c281"
                        }
                    }
                },
                {
                    "file": {
                        "mime_type": "application/pdf",
                        "name": "Invoice for Pharmtech.pdf",
                        "hash": {
                            "md5": "5873c7d37608e0d49bcaa6f32b6c731f",
                            "sha256": "2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca"
                        }
                    }
                }
            ]
        },
        "source": {
            "ip": "192.0.2.255",
            "address": "192.0.2.255"
        },
        "rule": {
            "name": "module.sandbox.threat"
        },
        "threat": {
            "enrichments": [
                {
                    "indicator": {
                        "first_seen": "2016-06-24T21:18:38.000Z",
                        "last_seen": "2016-06-24T21:18:38.000Z",
                        "reference": "https://threatinsight.proofpoint.com/#/73aa0499-dfc8-75eb-1de8-a471b24a2e75/threat/u/2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca",
                        "type": "file",
                        "file": {
                            "hash": {
                                "sha256": "2fab740f143fc1aa4c1cd0146d334c5593b1428f6d062b2c406e5efe8abe95ca"
                            }
                        }
                    }
                },
                {
                    "indicator": {
                        "first_seen": "2016-06-24T21:18:07.000Z",
                        "last_seen": "2016-06-24T21:18:07.000Z",
                        "reference": "https://threatinsight.proofpoint.com/#/73aa0499-dfc8-75eb-1de8-a471b24a2e75/threat/u/3ba97fc852c66a7ba761450edfdfb9f4ffab74715b591294f78b5e37a76481aa",
                        "type": "domain-name",
                        "url": {
                            "domain": "badsite.zz"
                        }
                    }
                }
            ]
        },
        "proofpoint": {
            "tap": {
                "modules": [
                    "pdr",
                    "sandbox",
                    "spam",
                    "urldefense"
                ],
                "cluster": {
                    "id": "pharmtech_hosted"
                },
                "email": {
                    "to": {
                        "address": [
                            "clark.kent@pharmtech.zz",
                            "diana.prince@pharmtech.zz"
                        ]
                    }
                },
                "threat": {
                    "scores": {
                        "spam": 4,
                        "impostor": 0,
                        "malware": 100,
                        "phish": 46
                    },
                    "classifications": [
                        "malware"
                    ]
                }
            }
        }
    }
    	
	```





## Extracted Fields

The following table lists the fields that are extracted, normalized under the ECS format, analyzed and indexed by the parser. It should be noted that infered fields are not listed.

| Name | Type | Description                |
| ---- | ---- | ---------------------------|
|`@timestamp` | `date` | Date/time when the event originated. |
|`email.attachments` | `array` | None |
|`email.cc.address` | `keyword` | None |
|`email.from.address` | `keyword` | None |
|`email.local_id` | `keyword` | None |
|`email.message_id` | `keyword` | None |
|`email.reply_to.address` | `keyword` | None |
|`email.sender.address` | `keyword` | None |
|`email.subject` | `keyword` | None |
|`email.to.address` | `keyword` | None |
|`email.x_mailer` | `keyword` | None |
|`event.action` | `keyword` | The action captured by the event. |
|`event.category` | `keyword` | Event category. The second categorization field in the hierarchy. |
|`event.dataset` | `keyword` | Name of the dataset. |
|`event.kind` | `keyword` | The kind of the event. The highest categorization field in the hierarchy. |
|`event.type` | `keyword` | Event type. The third categorization field in the hierarchy. |
|`observer.product` | `keyword` | The product name of the observer. |
|`observer.vendor` | `keyword` | Vendor name of the observer. |
|`proofpoint.tap.cluster.id` | `keyword` | None |
|`proofpoint.tap.email.to.address` | `array` | None |
|`proofpoint.tap.modules` | `array` | None |
|`proofpoint.tap.threat.classifications` | `array` | None |
|`proofpoint.tap.threat.scores.impostor` | `number` | None |
|`proofpoint.tap.threat.scores.malware` | `number` | None |
|`proofpoint.tap.threat.scores.phish` | `number` | None |
|`proofpoint.tap.threat.scores.spam` | `number` | None |
|`rule.name` | `keyword` | Rule name |
|`source.ip` | `ip` | IP address of the source. |
|`threat.enrichments` | `array` | None |
|`url.original` | `wildcard` | Unmodified original url as seen in the event source. |
|`user_agent.original` | `keyword` | Unparsed user_agent string. |

