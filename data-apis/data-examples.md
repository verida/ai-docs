---
icon: table
---

# Data examples

## Chat Group

Here's an example of a chat group JSON object. This is for a Telegram private chat and will be different for different types of chat groups.

```json
{
      "_id": "telegram-456049390-969538878",
      "sourceApplication": "https://telegram.com",
      "sourceId": "969538878",
      "sourceData": {
        "_": "chat",
        "id": 969538878,
        "type": {
          "_": "chatTypePrivate",
          "user_id": 969538878
        },
        "title": "",
        "accent_color_id": 0,
        "background_custom_emoji_id": "0",
        "profile_accent_color_id": -1,
        "profile_background_custom_emoji_id": "0",
        "permissions": {
          "_": "chatPermissions",
          "can_send_basic_messages": true,
          "can_send_audios": true,
          "can_send_documents": true,
          "can_send_photos": true,
          "can_send_videos": true,
          "can_send_video_notes": true,
          "can_send_voice_notes": true,
          "can_send_polls": true,
          "can_send_other_messages": true,
          "can_add_link_previews": true,
          "can_change_info": false,
          "can_invite_users": false,
          "can_pin_messages": true,
          "can_create_topics": false
        },
        "last_message": {
          "_": "message",
          "id": 73545023488,
          "sender_id": {
            "_": "messageSenderUser",
            "user_id": 969538878
          },
          "chat_id": 969538878,
          "is_outgoing": false,
          "is_pinned": false,
          "is_from_offline": false,
          "can_be_saved": true,
          "has_timestamped_media": true,
          "is_channel_post": false,
          "is_topic_message": false,
          "contains_unread_mention": false,
          "date": 1733217396,
          "edit_date": 0,
          "unread_reactions": [],
          "message_thread_id": 0,
          "saved_messages_topic_id": 0,
          "self_destruct_in": 0,
          "auto_delete_in": 0,
          "via_bot_user_id": 0,
          "sender_business_bot_user_id": 0,
          "sender_boost_count": 0,
          "author_signature": "",
          "media_album_id": "0",
          "effect_id": "0",
          "has_sensitive_content": false,
          "restriction_reason": "",
          "content": {
            "_": "messageText",
            "text": {
              "_": "formattedText",
              "text": "Hey good day. I am a marketing manager and content producer on YouTube.",
              "entities": [
                {
                  "_": "textEntity",
                  "offset": 264,
                  "length": 29,
                  "type": {
                    "_": "textEntityTypeUrl"
                  }
                },
                {
                  "_": "textEntity",
                  "offset": 295,
                  "length": 25,
                  "type": {
                    "_": "textEntityTypeUrl"
                  }
                }
              ]
            },
            "link_preview": {
              "_": "linkPreview",
              "url": "http://www.youtube.com/@NewCrypto",
              "display_url": "youtube.com/channel/...",
              "site_name": "YouTube",
              "title": "New Crypto",
              "description": {
                "_": "formattedText",
                "text": "🤙 Hello welcome to my channel I'm New Crypto",
                "entities": [
                  {
                    "_": "textEntity",
                    "offset": 419,
                    "length": 27,
                    "type": {
                      "_": "textEntityTypeUrl"
                    }
                  },
                  {
                    "_": "textEntity",
                    "offset": 454,
                    "length": 22,
                    "type": {
                      "_": "textEntityTypeEmailAddress"
                    }
                  },
                  {
                    "_": "textEntity",
                    "offset": 483,
                    "length": 24,
                    "type": {
                      "_": "textEntityTypeEmailAddress"
                    }
                  }
                ]
              },
              "author": "",
              "type": {
                "_": "linkPreviewTypePhoto",
                "photo": {
                  "_": "photo",
                  "has_stickers": false,
                  "minithumbnail": {
                    "_": "minithumbnail",
                    "width": 40,
                    "height": 40,
                    "data": "/9j/4AAQSk...//Z"
                  },
                  "sizes": [
                    {
                      "_": "photoSize",
                      "type": "m",
                      "photo": {
                        "_": "file",
                        "id": 2540,
                        "size": 20616,
                        "expected_size": 20616,
                        "local": {
                          "_": "localFile",
                          "path": "",
                          "can_be_downloaded": true,
                          "can_be_deleted": false,
                          "is_downloading_active": false,
                          "is_downloading_completed": false,
                          "download_offset": 0,
                          "downloaded_prefix_size": 0,
                          "downloaded_size": 0
                        },
                        "remote": {
                          "_": "remoteFile",
                          "id": "Ag...gQ",
                          "unique_id": "AQADxrUxG4eqhVNy",
                          "is_uploading_active": false,
                          "is_uploading_completed": true,
                          "uploaded_size": 20616
                        }
                      },
                      "width": 320,
                      "height": 320,
                      "progressive_sizes": []
                    },
                    {
                      "_": "photoSize",
                      "type": "x",
                      "photo": {
                        "_": "file",
                        "id": 2541,
                        "size": 83116,
                        "expected_size": 83116,
                        "local": {
                          "_": "localFile",
                          "path": "",
                          "can_be_downloaded": true,
                          "can_be_deleted": false,
                          "is_downloading_active": false,
                          "is_downloading_completed": false,
                          "download_offset": 0,
                          "downloaded_prefix_size": 0,
                          "downloaded_size": 0
                        },
                        "remote": {
                          "_": "remoteFile",
                          "id": "AgACA...NgQ",
                          "unique_id": "AQADxrUxG4eqhVN9",
                          "is_uploading_active": false,
                          "is_uploading_completed": true,
                          "uploaded_size": 83116
                        }
                      },
                      "width": 800,
                      "height": 800,
                      "progressive_sizes": []
                    },
                    {
                      "_": "photoSize",
                      "type": "y",
                      "photo": {
                        "_": "file",
                        "id": 2542,
                        "size": 92438,
                        "expected_size": 92438,
                        "local": {
                          "_": "localFile",
                          "path": "",
                          "can_be_downloaded": true,
                          "can_be_deleted": false,
                          "is_downloading_active": false,
                          "is_downloading_completed": false,
                          "download_offset": 0,
                          "downloaded_prefix_size": 0,
                          "downloaded_size": 0
                        },
                        "remote": {
                          "_": "remoteFile",
                          "id": "AgACA....DNgQ",
                          "unique_id": "AQADxrUxG4eqhVN-",
                          "is_uploading_active": false,
                          "is_uploading_completed": true,
                          "uploaded_size": 92438
                        }
                      },
                      "width": 900,
                      "height": 900,
                      "progressive_sizes": [
                        11770,
                        26273,
                        37932,
                        55019
                      ]
                    }
                  ]
                }
              },
              "has_large_media": true,
              "show_large_media": false,
              "show_media_above_description": false,
              "skip_confirmation": true,
              "show_above_text": false,
              "instant_view_version": 0
            }
          }
        },
        "positions": [
          {
            "_": "chatPosition",
            "list": {
              "_": "chatListMain"
            },
            "order": "7444112032678351354",
            "is_pinned": false
          }
        ],
        "chat_lists": [
          {
            "_": "chatListMain"
          }
        ],
        "has_protected_content": false,
        "is_translatable": true,
        "is_marked_as_unread": false,
        "view_as_topics": false,
        "has_scheduled_messages": false,
        "can_be_deleted_only_for_self": true,
        "can_be_deleted_for_all_users": false,
        "can_be_reported": false,
        "default_disable_notification": false,
        "unread_count": 0,
        "last_read_inbox_message_id": 73545023488,
        "last_read_outbox_message_id": 0,
        "unread_mention_count": 0,
        "unread_reaction_count": 0,
        "notification_settings": {
          "_": "chatNotificationSettings",
          "use_default_mute_for": true,
          "mute_for": 0,
          "use_default_sound": true,
          "sound_id": "-1",
          "use_default_show_preview": true,
          "show_preview": false,
          "use_default_mute_stories": true,
          "mute_stories": false,
          "use_default_story_sound": true,
          "story_sound_id": "-1",
          "use_default_show_story_sender": true,
          "show_story_sender": true,
          "use_default_disable_pinned_message_notifications": true,
          "disable_pinned_message_notifications": false,
          "use_default_disable_mention_notifications": true,
          "disable_mention_notifications": false
        },
        "available_reactions": {
          "_": "chatAvailableReactionsAll",
          "max_reaction_count": 11
        },
        "message_auto_delete_time": 0,
        "theme_name": "",
        "video_chat": {
          "_": "videoChat",
          "group_call_id": 0,
          "has_participants": false
        },
        "reply_markup_message_id": 0,
        "client_data": ""
      },
      "schema": "https://common.schemas.verida.io/social/chat/group/v0.1.0/schema.json",
      "name": "New Crypto",
      "insertedAt": "2025-02-19T17:36:43.727Z",
      "newestId": "telegram-456049390-73545023488",
      "syncData": "[[\"73545023488\",\"73545023488\"]]",
      "_rev": "417-d41b598b5826c16d1f5cc85249740721",
      "modifiedAt": "2025-02-19T17:37:43.122Z",
      "signatures": {
        "did:vda:mainnet:0xa603b7b8af20c9a73329a165666520be27fe0c4c2?context=0xb3c1545890d337d6f281177e5e0d3c3ac5d3308a1d696022d907c0b514f87bf4": {
          "secp256k1": "0xbb5541cab6411ca1106fdf0e35894d1f5f15b35e713369c1d5a3037c7e243fa14426dbd9ae987fb5f92b60fd58446bfb1a985f5ef69ec1ef24eebf06146453171b"
        }
      }
    }
```

## Chat Message

```json
{
      "_id": "telegram-456049390-9997123584",
      "name": "Has the next API vers...",
      "groupId": "telegram-456049390--579961374",
      "groupName": "Verida Team",
      "type": "receive",
      "fromId": "225312638",
      "fromHandle": "StevieBlank",
      "fromName": "StevieBlank",
      "messageText": "Has the next API version been released yet?",
      "schema": "https://common.schemas.verida.io/social/chat/message/v0.1.0/schema.json",
      "sourceApplication": "https://telegram.com",
      "sourceId": "9997123584",
      "sourceData": {
        "_": "message",
        "id": 9997123584,
        "sender_id": {
          "_": "messageSenderUser",
          "user_id": 215312638
        },
        "chat_id": -579961374,
        "is_outgoing": false,
        "is_pinned": false,
        "is_from_offline": false,
        "can_be_saved": true,
        "has_timestamped_media": true,
        "is_channel_post": false,
        "is_topic_message": false,
        "contains_unread_mention": false,
        "date": 1618537454,
        "edit_date": 0,
        "unread_reactions": [],
        "message_thread_id": 0,
        "saved_messages_topic_id": 0,
        "self_destruct_in": 0,
        "auto_delete_in": 0,
        "via_bot_user_id": 0,
        "sender_business_bot_user_id": 0,
        "sender_boost_count": 0,
        "author_signature": "",
        "media_album_id": "0",
        "effect_id": "0",
        "has_sensitive_content": false,
        "restriction_reason": "",
        "content": {
          "_": "messageText",
          "text": {
            "_": "formattedText",
            "text": "Has the next API version been released yet?",
            "entities": []
          }
        }
      },
      "insertedAt": "2021-04-16T01:44:14.000Z",
      "sentAt": "2021-04-16T01:44:14.000Z",
      "modifiedAt": "2025-02-10T09:59:54.568Z",
      "signatures": {
        "did:vda:mainnet:0x1a4a7b8af20c9a73329a165666520be27fe0c4c2?context=0xb3c1545890d337d6f281177e5e0d3c3ac5d3308a1d696022d907c0b514f87bf4": {
          "secp256k1": "0xfb188241fc25c10b819dd105a0126e66de8b9b12765254f30bb08167a1c8eb1317138cca8f39cff458c4c096bbf800c45d426a2abcbba82358c11b64c8d9d0311c"
        }
      },
      "_rev": "1-8315fdd91bc77906ff7d876c856ebd08"
    }
```

