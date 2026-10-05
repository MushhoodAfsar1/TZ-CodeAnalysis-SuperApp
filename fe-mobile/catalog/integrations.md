---
kb_section: fe-mobile
type: catalog
ids: [FE-CAT-INT]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
updated: 2026-10-05
confidence: partial
---

# Integrations

Presence in `pubspec.yaml` at `6328b7254`. Call sites are not traced unless the confidence column says confirmed. Package versions are omitted. No keys or project IDs are recorded.

| ID | Integration | Evidence | Conf. |
|---|---|---|---|
| INT-0001 | Firebase Core, Analytics, Crashlytics, Messaging, Auth, Database, Performance | firebase_* packages in pubspec | inferred |
| INT-0002 | Sentry | sentry_flutter | inferred |
| INT-0003 | MoEngage | moengage_flutter | inferred |
| INT-0004 | Adjust | adjust_sdk | inferred |
| INT-0005 | Facebook App Events | facebook_app_events | inferred |
| INT-0006 | Biometrics | local_auth | inferred |
| INT-0007 | Location and maps | geolocator, google_maps_flutter | inferred |
| INT-0008 | QR scan | mobile_scanner | inferred |
| INT-0009 | Face detection | google_mlkit_face_detection | inferred |
| INT-0010 | In-app web view | flutter_inappwebview | inferred |
| INT-0011 | Local database (Floor) | floor | inferred |
| INT-0012 | HTTP client (Dio) | dio — used by NetworkManager | confirmed |
| INT-0013 | Local notifications | flutter_local_notifications | inferred |
| INT-0014 | Chatbot (Dialogflow) | dialogflow_grpc | inferred |
| INT-0015 | OTP autofill | otp_autofill | inferred |
| INT-0016 | Device contacts | flutter_native_contact_picker | inferred |
| INT-0017 | Camera and gallery | camera, image_picker | inferred |
| INT-0018 | WebSocket | web_socket_channel | inferred |
| INT-0019 | App tracking transparency | app_tracking_transparency | inferred |
| INT-0020 | External app / URL launch | url_launcher, external_app_launcher | inferred |
| INT-0021 | Payload crypto | encrypt, crypto — CryptoUtil | confirmed |

