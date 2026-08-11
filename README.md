# Nafl Queue 🌙

**A Seamless and Intuitively Managed System for Your Nafl (Voluntary) Prayers**

NaflQueue is a modern Windows desktop application built with **C# WinForms** and powered by **Google Firebase & Cloud Firestore**. It enables users to securely register, subscribe to tailored packages, search and book/cancel prayer slots in real-time, track spiritual progress via an integrated Tasbeeh counter, and receive instant booking notifications. It also provides a management interface for system administrators.

---

## ✨ Key Features

* **🔒 Secure Authentication:** Sign up, log in, and request password resets securely via Firebase Authentication.
* **💳 Subscription-Based Access:** Choose from three pricing tiers (Basic, Standard, Premium) that dynamically dictate the number of accessible prayer areas, slots, and maximum concurrent bookings.
* **🕌 Real-Time Prayer Slot Booking:** Reserve voluntary prayer slots across iconic sites with live availability synchronization via Firestore.
* **❌ Easy Booking Cancellation:** Release booked slots instantly with a single click, automatically opening availability for other pilgrims/worshipers.
* **📊 Unified User Dashboard:** Monitor active/past bookings, control prayer selections, view real-time notification alerts, and access other features from a centralized hub.
* **📿 Persistent Tasbeeh Counter:** Increment your daily prayers and dhikr with an auto-saving counter stored persistently in your cloud profile.
* **🔔 Real-Time Notifications:** View instant status updates regarding active bookings and cancellations via an in-app alert notification badge.
* **👑 Admin Controls:** Empower administrators to view active users and remove accounts directly using a specialized grid interface.

---

## 🛠️ Technology Stack

* **Front-End Engine:** Windows Forms (WinForms) / C# / .NET Framework 4.8
* **Database & Storage:** Google Cloud Firestore (NoSQL Document Store)
* **Identity Provider:** Google Firebase Authentication
* **Dependencies Management:** NuGet Package Manager
* **Serialization & APIs:** Newtonsoft.Json, gRPC, and Google Client Libraries

---

## 💾 Cloud Firestore Data Schema

NaflQueue relies on three primary document collections in Cloud Firestore:

### 1. `users` Collection
Each user document is identified by the user's unique Firebase Authentication UID (`userId`):
```json
{
"Username": "Sana",
"Age": 22,
"Phone": "505159623",
"Nationality": "Saudi Arabia",
"Email": "[EMAIL_ADDRESS]",
"Password": "[PASSWORD]",
"CreatedAt": "Timestamp",
"SubscriptionType": "Premium", // Basic, Standard, or Premium
"tasbeehCount": 234
}
```

### 2. `places` Collection
Stores details of worship places. Each place document contains a `slots` subcollection:
* **Document Path:** `/places/{PlaceName}` (e.g., `/places/Raudah`)
* **Subcollection Path:** `/places/{PlaceName}/slots`
* **Document Fields:**
```json
{
"time": "08:00 AM - 09:00 AM",
"booked": true // true or false
}
```

### 3. `bookings` Collection
Maintains active reservations for users. Documents use auto-generated Firestore IDs:
```json
{
"email": "[EMAIL_ADDRESS]",
"place": "Raudah",
"slot": "08:00 AM - 09:00 AM",
"bookedAt": "Timestamp"
}
```

---

## 📈 Subscription Pricing & Limits

| Subscription Tier | Cost | Accessible Areas | Max Slots Shown | Concurrent Bookings Allowed |
| :--- | :--- | :---: | :---: | :---: |
| **Basic** | 70 SAR / Month | 2 Areas | 6 Slots | 2 |
| **Standard** | 110 SAR / Month | 4 Areas | 9 Slots | 4 |
| **Premium** | 150 SAR / Month | 5 Areas | 15 Slots | 6 |

---

## ⚙️ Installation & Getting Started

### Prerequisites
* Windows 10/11 Operating System
* [Visual Studio 2022](https://visualstudio.microsoft.com/) (with *.NET desktop development* workload enabled)
* .NET Framework 4.8 SDK

### 1. Setup Firebase Configuration
To connect the application to your Firebase project:
1. Obtain your Firebase Service Account JSON credentials file from the Firebase Console (Settings -> Service Accounts).
2. Save the credential file in the project's output directory (e.g., `bin/Debug/`) and name it:
`naflqueue-firebase-adminsdk-fbsvc-dffb95e1ca.json`
3. If you wish to use password resets, obtain your Firebase Web API Key and update it in [Form1.cs](file:///d:/Downloads/NaflQueue-main/NaflQueue/Form1.cs#L92):
```csharp
string apiKey = "YOUR_FIREBASE_WEB_API_KEY";
```

### 2. Build and Run
1. Open the solution file NaflQueue.sln in Visual Studio.
2. Restore NuGet Packages:
* Right-click the Solution in Solution Explorer and select **Restore NuGet Packages**.
3. Set the configuration mode to `Debug` or `Release`.
4. Click the **Start** (F5) button in Visual Studio to build and launch the application.

---

### 🤝 Team NaflQueue

> **Minahil Rizwan · Abdullah Attique · Hamda Shahid**

Together, we designed and developed **Nafl Queue** as a collaborative software project, combining application development, cloud technologies, database management, and user-focused design.