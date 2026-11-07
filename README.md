# IRONFORGE Gym - Website

The public website of IRONFORGE Gym. Visitors can browse equipment, exercises, classes and coaches, check their BMI, compare membership plans in PKR, and join online with Easypaisa, JazzCash or cash at the gym. New memberships are saved to Firebase and appear in the staff panel.

## Folder structure

    ironforge-gym/
    ├── index.html
    ├── style.css
    ├── script.js
    ├── firebase-config.js      (Firebase keys, already filled in)
    └── images/
        ├── dumbbell.svg  barbell.svg  kettlebell.svg  treadmill.svg
        ├── bench.svg  battle-rope.svg  cable-machine.svg  weight-plates.svg
        └── payment/            (easypaisa-qr.png, jazzcash-qr.png)

## Features

- Dark and light theme that follows the device setting and remembers the visitor's choice
- Hero slideshow, equipment cards, exercise library with filters, weekly classes, coaches and a BMI calculator
- Membership plans in PKR with a monthly and yearly toggle (yearly saves 20%)
- Join form: full name, email and plan
- After joining, a payment step:
  - Monthly or Yearly billing (the amount updates automatically)
  - Easypaisa or JazzCash with a QR code, the account number and a transaction ID field
  - Cash at the gym (pay at the front desk)
- The membership is saved to Firebase when the payment step is confirmed
- Membership ID and a WhatsApp confirmation link after confirming
- Responsive layout and reduced-motion support

## Plan prices (PKR)

| Plan  | Monthly | Yearly (per month) | Yearly total |
|-------|---------|--------------------|--------------|
| Basic | 4,000   | 3,200              | 38,400       |
| Pro   | 7,000   | 5,600              | 67,200       |
| Elite | 12,000  | 9,600              | 115,200      |

To change prices, edit the `PR` line in `script.js` (monthly price first, then the yearly per-month price).

## Payment QR codes

Download your QR codes from the Easypaisa and JazzCash apps and save them as:

    images/payment/easypaisa-qr.png
    images/payment/jazzcash-qr.png

If a QR image is missing, the page still shows the account number.

## Firebase setup

This site uses the same Firebase project as the other sites (`hasan-mart`). Memberships are saved in the `gymMembers` collection. The Firebase config is already in `firebase-config.js`.

1. In Firebase go to Firestore Database > Rules, paste the rules below (replace `STAFF_EMAIL` with the staff email) and click Publish:

        rules_version = '2';
        service cloud.firestore {
          match /databases/{database}/documents {
            match /orders/{id} {
              allow create: if true;
              allow read, update: if request.auth != null
                && request.auth.token.email == 'STAFF_EMAIL';
            }
            match /restaurantOrders/{id} {
              allow create: if true;
              allow read, update: if request.auth != null
                && request.auth.token.email == 'STAFF_EMAIL';
            }
            match /courseEnrollments/{id} {
              allow create: if true;
              allow read, update: if request.auth != null
                && request.auth.token.email == 'STAFF_EMAIL';
            }
            match /courseInquiries/{id} {
              allow create: if true;
              allow read, update: if request.auth != null
                && request.auth.token.email == 'STAFF_EMAIL';
            }
            match /hotelBookings/{id} {
              allow create: if true;
              allow read, update: if request.auth != null
                && request.auth.token.email == 'STAFF_EMAIL';
            }
            match /gymMembers/{id} {
              allow create: if true;
              allow read, update: if request.auth != null
                && request.auth.token.email == 'STAFF_EMAIL';
            }
          }
        }

2. Make sure `syedhasanshahqadri-ops.github.io` is listed under Authentication > Settings > Authorized domains.

Always paste the complete rules. Removing a block stops the matching site from working.

Until Firebase is connected, the site runs in demo mode and the gym will not receive memberships.

## Changing details

- Phone number: the Join section in `index.html` (and the `WA` value in `script.js` for WhatsApp, in international format without a leading 0 or +)
- Address and opening hours: the Join section in `index.html`
- Easypaisa and JazzCash numbers: the `NUM` line in `script.js`
- Equipment, exercises, classes and coaches: the data arrays in `script.js`
- Colours and fonts: the variables at the top of `style.css`

## Publishing on GitHub Pages

1. Create a repository named `ironforge-gym`.
2. Upload all the files, keeping the `images` folder.
3. Go to Settings > Pages, choose the `main` branch and the root folder, then save.
4. Your link: `https://syedhasanshahqadri-ops.github.io/ironforge-gym/`

## Notes

- The join form collects only the name and email, so the gym contacts members by email.
- Delete test memberships from the Firebase console before going live.
