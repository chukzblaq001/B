# BIOLEARN — Free Offline Biology Learning App

A beginner-friendly Biology learning PWA made with plain HTML, CSS and JavaScript. No paid services or JavaScript frameworks are required.

## What is included in this starter

- Responsive layout for Android phones and Windows computers
- Sample lessons spanning JSS 1 through University 400
- Search and level filters
- Lesson notes and simple built-in educational diagrams
- Multiple-choice quizzes with instant marking and explanations
- Local progress, quiz score and bookmark saving with `localStorage`
- Offline Biology tutor that searches bundled lesson content (no internet or API key needed)
- PWA manifest and service worker for offline caching
- Install button where supported by the browser

## Run it on your Windows computer

**Recommended:** Use VS Code with the free Live Server extension.

1. Extract `BIOLEARN.zip` to a folder you can find, such as `Documents/BIOLEARN`.
2. Open VS Code.
3. Select **File → Open Folder** and choose the extracted `BIOLEARN` folder.
4. In the Extensions panel, search for **Live Server** and install it.
5. Open `index.html`, right-click inside it, and choose **Open with Live Server**.
6. A browser tab should open. Try a lesson, bookmark a topic and take a quiz.

Do not open `index.html` by double-clicking it if you want to test offline/PWA installation: service workers require `localhost` or HTTPS.

## Test offline on your computer

1. Open the app through Live Server.
2. Let the page load completely once.
3. In Chrome, open Developer Tools → Application → Service Workers and check that the service worker is active.
4. In Developer Tools → Network, select **Offline**, then refresh. The app should load from its cache.

Browser menus can vary. Test offline after each major update.

## Use it on Android

### Local testing
Your computer's `localhost` address is not automatically accessible from your phone. For the easiest phone install, publish the folder to a free HTTPS static host, such as GitHub Pages, then open the site on Android Chrome. This initial publishing step needs internet.

### Install
1. Open the hosted HTTPS app in Chrome.
2. Load it once while online and wait for it to finish.
3. Open Chrome's three-dot menu.
4. Choose **Install app** or **Add to Home screen** if shown.
5. Launch BIOLEARN from the new home-screen icon.
6. Test it in airplane mode.

PWA install prompts vary by browser/device. Some browsers may display “Add to Home screen” rather than “Install app”.

## Add more lessons and questions

Open `app.js`. Each lesson is one object inside the `LESSONS` array. Give each lesson a unique `id`, a `level`, `title`, `summary`, `sections`, and `quiz` array. A quiz question uses:

```js
{
  q: "Your question?",
  options: ["Option A", "Option B", "Option C", "Option D"],
  answer: 1,
  explanation: "Why option B is correct."
}
```

The `answer` is a zero-based index: `0` means the first option, `1` the second, and so on. Each included lesson currently has three sample questions. Add more to expand the question bank.

## Offline and privacy notes

- Lesson text and quiz data in this starter are bundled in `app.js`, so they do not require an internet request.
- Progress is saved in browser `localStorage` on the device/browser profile. Clearing site data may erase it; it does not automatically sync to other devices.
- The service worker caches the app shell. Increment `CACHE_NAME` in `service-worker.js` when you make changes so browsers can fetch the new version.
- The app does not currently have online accounts, cloud sync, audio/video downloads or an admin content editor.
- The sample lessons are a starting point, not a complete authoritative national curriculum. Verify and expand content against current NERDC, WAEC, NECO, JAMB and relevant university syllabuses before presenting the app as comprehensive exam preparation.
- Use original questions or properly licensed material. Do not upload copyrighted exam papers without permission.

## Folder contents

- `index.html` — page structure
- `styles.css` — layout and styling
- `app.js` — lessons, quizzes, progress and interactions
- `manifest.json` — installable app metadata
- `service-worker.js` — offline cache
- `icon.svg` — app icon


## Offline Tutor and real AI

The built-in tutor answers using the lesson material bundled in `app.js`. It works offline and makes no network requests, but it is a simple local knowledge helper, not a generative AI model.

For a genuine online AI tutor, connect a provider through a secure server/backend that you control. Do **not** paste a private API key into `app.js` or any file downloaded by the browser; users can inspect those files. Keep the offline tutor as a fallback when there is no internet. Any AI provider may have limits, require an account, or charge for use.


## Expanded curriculum roadmap

The updated app includes a searchable topic checklist for JSS 1–3 foundations, SS 1–3 Biology, and a general University 100–400 Biology pathway. It also includes dedicated JAMB UTME, WAEC and NECO preparation checklists and links to official resources. The curriculum map is stored in `curriculum-data.js`, separate from the main app code.

**Important curriculum boundaries:** NERDC JSS1–3 is Basic Science and Technology rather than a standalone Biology subject. University course titles and requirements vary by programme and institution. Use the current official syllabus for your examination year; the topic roadmap is a structured study guide, not a verbatim copy of every syllabus. NECO and WAEC should be checked separately.

### Official reference links
- NERDC e-Curriculum: https://nerdc.org.ng/CurriculumView.aspx
- JAMB Biology syllabus: https://ibass.jamb.gov.ng/assets/uploads/Biology.pdf
- WAEC e-Learning: https://www.waeconline.org.ng/e-learning/
- NECO: https://neco.gov.ng/

The roadmap adds topic coverage and exam-preparation structure, but it does not magically create full detailed notes or verified questions for every listed topic. The included lesson cards remain the detailed sample lessons; add vetted notes, diagrams and original questions topic by topic before advertising the app as a complete syllabus/course.


## Detailed lesson pack

This build adds `detailed-lessons.js`, an offline lesson collection with original explanations and multiple-choice practice questions. It covers core junior-secondary foundations, senior-secondary Biology and selected University 100–400 themes. The curriculum checklist is broader than the detailed lesson library; topics not yet written as full lessons remain roadmap entries. Questions in this pack are original practice questions, not represented as verbatim past examination questions.

### Exam preparation

Use the official current syllabus and instructions for each examination. JAMB UTME Biology is available through the JAMB IBASS syllabus portal. WAEC provides Biology past-paper resources and examiner feedback through its e-learning portal. Confirm the applicable NECO syllabus and exam instructions through NECO. University modules vary by institution and programme; the university pathway is a general study roadmap rather than a national universal syllabus.

Official references:
- NERDC e-Curriculum: https://nerdc.org.ng/CurriculumView.aspx
- JAMB IBASS Biology syllabus: https://ibass.jamb.gov.ng/assets/uploads/Biology.pdf
- WAEC Biology e-learning: https://www.waeconline.org.ng/e-learning/Biology/Biomain.html
- NECO official site: https://neco.gov.ng/


See `EXAM_QUESTION_BANK.md` for 30 original objective questions with an answer key, structured theory prompts, practical exercises and marking guidance. These are revision materials, not verbatim past papers.


## Full curriculum expansion (added)
- Curriculum roadmap contains 235 listed topics across JSS 1–3, SS 1–3 and University 100–400.
- Each listed topic is connected to a study lesson with learning objectives, topic guidance, key words, revision summary and exam-technique notes.
- Each topic offers a 30-question practice bank. The general quiz can draw up to 40 questions.
- A subset of questions are reusable topic-focused revision/learning-strategy questions and the pack contains original practice items; these are not represented as verified past WAEC/NECO/JAMB questions.
- JSS content is foundational Basic Science and Technology; university topics are a general roadmap, not a universal institution-specific syllabus. Check the current official syllabus and course outline.
- Open `index.html` with Live Server. Keep `curriculum-data.js`, `detailed-lessons.js`, `full-curriculum.js`, `app.js`, and `styles.css` in the same folder.


### Content quality note
The full pack gives every roadmap topic its own lesson entry and 30-question practice set. Some question slots are general revision/exam-technique questions and some factual questions are reused within the same broad Biology domain; they are original practice items, not a guarantee of 7,050 individually syllabus-validated questions. Review the material with current official JAMB, WAEC, NECO and institution-specific syllabuses before using it as the sole exam resource.


## Dedicated exam preparation added
- JAMB UTME Biology: syllabus focus checklist, timed multiple-choice practice and 40-question mock exams.
- WAEC Biology: objective practice, timed mock exams, theory answer outlines and practical/specimen skill workshops.
- NECO Biology: a separate pathway with objective practice, timed mocks and theory/practical skill workshops. Confirm the applicable current NECO syllabus and exam instructions through NECO.
- Objective questions are drawn from the app's bundled original Biology question bank and are shuffled for attempts. The mock mode uses 40 questions and a 45-minute timer; practice mode uses 20 questions.
- Theory/practical prompts include expandable answer outlines or marking guidance. These are original practice materials, not verified past papers or a guarantee of exact official exam format.
- New file: `exam-prep.js`; service-worker cache version was updated.
