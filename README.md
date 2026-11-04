<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>PW Tracker 360 • CBSE Commerce, Science & Arts Study Planner</title>
  <meta name="description" content="PW Tracker 360 - Complete CBSE Class 11 & 12 Study, Backlog, Live Class, DPP & Test Planner." />
  <meta name="theme-color" content="#5A4BDA" />

  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, sans-serif;
      background-color: #F8F9FB;
      color: #111827;
      -webkit-tap-highlight-color: transparent;
    }
    .pw-purple { background-color: #5A4BDA; }
    .pw-purple-text { color: #5A4BDA; }
    .pw-card-shadow { box-shadow: 0 1px 3px 0 rgba(16, 24, 40, 0.06), 0 1px 2px -1px rgba(16, 24, 40, 0.06); }
    .no-scrollbar::-webkit-scrollbar { display: none; }
    .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
  </style>
</head>
<body>
  <div id="root"></div>

  <script type="text/babel">
    const { useState, useEffect, useMemo } = React;

    const STORAGE_KEY = 'pw_tracker_360_final_master_v1';

    const INITIAL_BATCH_DATA = {
      commerce12: {
        id: 'commerce12',
        shortName: 'Kautilya 12...',
        fullName: 'Kautilya Commerce Class 12 (CBSE)',
        batchCode: 'PW-KAUTILYA-12',
        testTitle: 'Practice Test 04',
        testMeta: 'TEST • 3H • 75 QUESTIONS • 300 MARKS',
        testSyllabus: 'Accounting for Partnership Fundamentals • Goodwill & Change in PSR • National Income & Aggregates • Principles of Management',
        aitsAlert: { title: 'All India Test Series 02 is on Sat, 14 Nov', remaining: 14, total: 30 },
        backlogAlert: { subject: 'Accountancy', hours: '9h', classesCount: 9 },
        subjects: [
          {
            id: 'acc',
            name: 'Accountancy',
            borderClass: 'border-l-[#0EA5E9]',
            dashedClass: 'border-l-[#0EA5E9]',
            textClass: 'text-[#0284C7]',
            subText: '2 teachers - follow one, or more',
            teachers: [
              {
                id: 'acc_t1', initial: 'R', name: 'CA Rajat Arora Sir', lectures: 101, dpps: 33, videoHours: 171,
                chapters: [
                  'Ch 01 : Accounting for Partnership Fundamentals',
                  'Ch 02 : Goodwill: Nature & Valuation',
                  'Ch 03 : Change in Profit Sharing Ratio',
                  'Ch 04 : Admission of a Partner',
                  'Ch 05 : Retirement & Death of a Partner',
                  'Ch 06 : Dissolution of Partnership Firm',
                  'Ch 07 : Accounting for Share Capital',
                  'Ch 08 : Issue & Redemption of Debentures',
                  'Ch 09 : Financial Statements & Ratio Analysis',
                  'Ch 10 : Cash Flow Statement'
                ]
              },
              {
                id: 'acc_t2', initial: 'N', name: 'CA Nitin Goel Sir', lectures: 88, dpps: 29, videoHours: 149,
                chapters: [
                  'Ch 01 : Partnership Fundamentals & Goodwill',
                  'Ch 02 : Reconstitution - Admission, Retirement & Death',
                  'Ch 03 : Dissolution of Firm',
                  'Ch 04 : Accounting for Companies (Shares & Debentures)',
                  'Ch 05 : Analysis of Financial Statements',
                  'Ch 06 : Cash Flow Statement'
                ]
              }
            ]
          },
          {
            id: 'eco',
            name: 'Economics',
            borderClass: 'border-l-[#10B981]',
            dashedClass: 'border-l-[#10B981]',
            textClass: 'text-[#059669]',
            subText: '2 teachers - follow one, or more',
            teachers: [
              {
                id: 'eco_t1', initial: 'L', name: 'Love Kaushik Sir', lectures: 78, dpps: 28, videoHours: 124,
                chapters: [
                  'Ch 01 : Circular Flow & National Income Aggregates',
                  'Ch 02 : Money and Banking',
                  'Ch 03 : Determination of Income & Employment',
                  'Ch 04 : Government Budget and the Economy',
                  'Ch 05 : Balance of Payments & Foreign Exchange',
                  'Ch 06 : Indian Economy on the Eve of Independence',
                  'Ch 07 : LPG Reforms 1991 & Human Capital Formation',
                  'Ch 08 : Rural Development, Employment & Sustainable Dev'
                ]
              },
              {
                id: 'eco_t2', initial: 'T', name: 'Tanya Munjal Ma\'am', lectures: 70, dpps: 25, videoHours: 112,
                chapters: [
                  'Ch 01 : Macroeconomics - National Income & Money',
                  'Ch 02 : Aggregate Demand, Govt Budget & BOP',
                  'Ch 03 : Indian Economic Development (1947-1991)',
                  'Ch 04 : Current Challenges of Indian Economy',
                  'Ch 05 : Comparative Development: India, China & Pakistan'
                ]
              }
            ]
          },
          {
            id: 'bst',
            name: 'Business Studies',
            borderClass: 'border-l-[#F43F5E]',
            dashedClass: 'border-l-[#F97316]',
            textClass: 'text-[#C2410C]',
            subText: '1 teacher',
            teachers: [
              {
                id: 'bst_t1', initial: 'D', name: 'Disha Khare Ma\'am', lectures: 66, dpps: 24, videoHours: 102,
                chapters: [
                  'Ch 01 : Nature & Significance of Management',
                  'Ch 02 : Principles of Management (Fayol & Taylor)',
                  'Ch 03 : Business Environment & Planning',
                  'Ch 04 : Organising & Staffing',
                  'Ch 05 : Directing & Controlling',
                  'Ch 06 : Financial Management & Financial Markets',
                  'Ch 07 : Marketing Management & Consumer Protection'
                ]
              }
            ]
          },
          {
            id: 'maths',
            name: 'Applied / Core Maths',
            borderClass: 'border-l-[#10B981]',
            dashedClass: 'border-l-[#10B981]',
            textClass: 'text-[#059669]',
            subText: '2 teachers - follow one, or more',
            teachers: [
              {
                id: 'mat_t1', initial: 'R', name: 'Rohit Solanki Sir (Applied)', lectures: 86, dpps: 30, videoHours: 142,
                chapters: [
                  'Ch 01 : Numbers, Quantification & Numerical Applications',
                  'Ch 02 : Matrices & Determinants',
                  'Ch 03 : Differentiation & Applications of Derivatives',
                  'Ch 04 : Integrals & Differential Equations',
                  'Ch 05 : Probability Distributions',
                  'Ch 06 : Financial Mathematics (EMI, Sinking Fund, CAGR)',
                  'Ch 07 : Linear Programming & Time Series'
                ]
              },
              {
                id: 'mat_t2', initial: 'S', name: 'Shivang Agarwal Sir (Core)', lectures: 96, dpps: 34, videoHours: 158,
                chapters: [
                  'Ch 01 : Relations, Functions & ITF',
                  'Ch 02 : Matrices & Determinants',
                  'Ch 03 : Continuity, Differentiability & AOD',
                  'Ch 04 : Integrals & Differential Equations',
                  'Ch 05 : Vectors, 3D Geometry, LPP & Probability'
                ]
              }
            ]
          }
        ],
        recordedTasks: [
          {
            id: 'c12_rec_1', subject: 'ACCOUNTANCY', teacher: 'CA Rajat Arora Sir', borderClass: 'border-l-[#0EA5E9]', textClass: 'text-[#0284C7]',
            isOverdue: true, type: 'LECTURE', title: '10 : Admission of a Partner (Part 3)', chapter: 'Ch 04 : Admission of a Partner',
            durationSpeed: '1h 37m', duration1x: '2h 25m at 1x', watchedPct: 0, section: 'today'
          },
          {
            id: 'c12_rec_2', subject: 'ECONOMICS', teacher: 'Love Kaushik Sir', borderClass: 'border-l-[#10B981]', textClass: 'text-[#059669]',
            isOverdue: true, type: 'LECTURE', title: '08 : National Income Aggregates (Part 2)', chapter: 'Ch 01 : Circular Flow & National Income',
            durationSpeed: '1h 1m', duration1x: '1h 32m at 1x', watchedPct: 0, section: 'today'
          },
          {
            id: 'c12_rec_3', subject: 'MATHS', teacher: 'Rohit Solanki Sir', borderClass: 'border-l-[#10B981]', textClass: 'text-[#059669]',
            isOverdue: true, type: 'LECTURE', title: 'Matrices & Cramer\'s Rule', chapter: 'Matrices & Determinants',
            durationSpeed: '1h 10m', duration1x: '1h 45m at 1x', watchedPct: 38, section: 'leftover'
          }
        ],
        liveTasks: [
          {
            id: 'c12_live_1', subject: 'ACCOUNTANCY', teacher: 'CA Rajat Arora Sir', borderClass: 'border-l-[#0EA5E9]', textClass: 'text-[#0284C7]',
            title: 'Revaluation Account & Partner\'s Capital', timeSlot: '9:00 – 10:45 pm', unlockAfter: '10:45 pm', chapter: 'Admission of a Partner', duration: '1h 45m', canJoinNow: true
          },
          {
            id: 'c12_live_2', subject: 'BUSINESS STUDIES', teacher: 'Disha Khare Ma\'am', borderClass: 'border-l-[#F43F5E]', textClass: 'text-[#BE123C]',
            title: 'Principles of Management - Fayol & Taylor', timeSlot: '11:15 – 1:00 am', unlockAfter: '1:00 am', chapter: 'Principles of Management', duration: '1h 45m', canJoinNow: false
          }
        ],
        practiceDpp: { id: 'c12_dpp_1', subject: 'ACCOUNTANCY', teacher: 'CA Rajat Arora Sir', title: 'Admission of a Partner DPP 04', chapter: 'Admission of a Partner', duration: '1h' },
        tomorrowRecorded: [
          { subject: 'ECONOMICS', teacher: 'Love Kaushik Sir', dashedClass: 'border-l-[#10B981]', textClass: 'text-[#059669]', line: 'Ch 02 : Money and Banking • 09 : Credit Creation...' },
          { subject: 'BUSINESS STUDIES', teacher: 'Disha Khare Ma\'am', dashedClass: 'border-l-[#F97316]', textClass: 'text-[#C2410C]', line: 'Ch 02 : Principles of Management • 04 : Taylor\'s Principles...' }
        ],
        tomorrowLive: [
          { time: '4:00 pm', subject: 'ECONOMICS', teacher: 'Love Kaushik Sir', dashedClass: 'border-l-[#10B981]', textClass: 'text-[#059669]', topic: 'Money Multiplier...' },
          { time: '6:15 pm', subject: 'ACCOUNTANCY', teacher: 'CA Rajat Arora Sir', dashedClass: 'border-l-[#0EA5E9]', textClass: 'text-[#0284C7]', topic: 'Share Capital...' }
        ],
        questions: [
          { q: '1. In the absence of a Partnership Deed, interest on a partner\'s loan is allowed at:', options: ['6% p.a.', '10% p.a.', '12% p.a.', 'No interest is allowed'], ans: 0, chapter: 'Accountancy • Partnership Fundamentals' },
          { q: '2. If the Legal Reserve Ratio (LRR) is 20%, what is the Money Multiplier?', options: ['4', '5', '10', '20'], ans: 1, chapter: 'Economics • Money & Banking' },
          { q: '3. Which principle of management states "One Head and One Plan" for a group of activities having the same objective?', options: ['Unity of Command', 'Unity of Direction', 'Scalar Chain', 'Order'], ans: 1, chapter: 'Business Studies • Principles of Management' },
          { q: '4. Premium for Goodwill brought in by a new partner is shared by old partners in their:', options: ['Old Profit Sharing Ratio', 'New Profit Sharing Ratio', 'Sacrificing Ratio', 'Capital Ratio'], ans: 2, chapter: 'Accountancy • Admission of a Partner' },
          { q: '5. Which of the following is a transfer payment (not included in National Income)?', options: ['Free meals to employees', 'Old-age pension', 'Commission on sale of land', 'Royalty'], ans: 1, chapter: 'Economics • National Income' }
        ]
      },
      commerce11: {
        id: 'commerce11',
        shortName: 'Aarambh 11...',
        fullName: 'Aarambh Commerce Class 11 (CBSE)',
        batchCode: 'PW-AARAMBH-11',
        testTitle: 'Practice Test 04',
        testMeta: 'TEST • 3H • 75 QUESTIONS • 300 MARKS',
        testSyllabus: 'Accounting Equation & Journal • Consumer Equilibrium & Demand • Forms of Business Organisation',
        aitsAlert: { title: 'All India Test Series 02 is on Sat, 14 Nov', remaining: 10, total: 24 },
        backlogAlert: { subject: 'Statistics', hours: '6h', classesCount: 6 },
        subjects: [
          {
            id: 'acc11', name: 'Accountancy (Class 11)', borderClass: 'border-l-[#0EA5E9]', dashedClass: 'border-l-[#0EA5E9]', textClass: 'text-[#0284C7]', subText: '1 teacher',
            teachers: [{ id: 'a11_t1', initial: 'R', name: 'CA Rajat Arora Sir', lectures: 84, dpps: 28, videoHours: 140, chapters: ['Ch 01 : Introduction to Accounting', 'Ch 02 : Accounting Equation', 'Ch 03 : Journal & Ledger', 'Ch 04 : Cash Book & Subsidiary Books', 'Ch 05 : Bank Reconciliation Statement (BRS)', 'Ch 06 : Depreciation', 'Ch 07 : Financial Statements of Sole Proprietorship'] }]
          },
          {
            id: 'eco11', name: 'Economics (Micro + Stats)', borderClass: 'border-l-[#10B981]', dashedClass: 'border-l-[#10B981]', textClass: 'text-[#059669]', subText: '1 teacher',
            teachers: [{ id: 'e11_t1', initial: 'L', name: 'Love Kaushik Sir', lectures: 74, dpps: 25, videoHours: 120, chapters: ['Ch 01 : Consumer\'s Equilibrium', 'Ch 02 : Theory of Demand & Elasticity', 'Ch 03 : Production Function & Cost', 'Ch 04 : Measures of Central Tendency', 'Ch 05 : Correlation & Index Numbers'] }]
          },
          {
            id: 'bst11', name: 'Business Studies (Class 11)', borderClass: 'border-l-[#F43F5E]', dashedClass: 'border-l-[#F97316]', textClass: 'text-[#C2410C]', subText: '1 teacher',
            teachers: [{ id: 'b11_t1', initial: 'D', name: 'Disha Khare Ma\'am', lectures: 60, dpps: 20, videoHours: 95, chapters: ['Ch 01 : Nature and Purpose of Business', 'Ch 02 : Forms of Business Organisation', 'Ch 03 : Public, Private & Global Enterprises', 'Ch 04 : Business Services', 'Ch 05 : Sources of Business Finance'] }]
          }
        ],
        recordedTasks: [
          { id: 'c11_rec_1', subject: 'ACCOUNTANCY', teacher: 'CA Rajat Arora Sir', borderClass: 'border-l-[#0EA5E9]', textClass: 'text-[#0284C7]', isOverdue: true, type: 'LECTURE', title: '07 : Bank Reconciliation Statement (Part 2)', chapter: 'Ch 05 : Bank Reconciliation Statement', durationSpeed: '1h 20m', duration1x: '2h 00m at 1x', watchedPct: 0, section: 'today' },
          { id: 'c11_rec_2', subject: 'ECONOMICS', teacher: 'Love Kaushik Sir', borderClass: 'border-l-[#10B981]', textClass: 'text-[#059669]', isOverdue: true, type: 'LECTURE', title: 'Price Elasticity of Demand', chapter: 'Ch 02 : Theory of Demand', durationSpeed: '1h 05m', duration1x: '1h 38m at 1x', watchedPct: 38, section: 'leftover' }
        ],
        liveTasks: [
          { id: 'c11_live_1', subject: 'ACCOUNTANCY', teacher: 'CA Rajat Arora Sir', borderClass: 'border-l-[#0EA5E9]', textClass: 'text-[#0284C7]', title: 'Depreciation - Straight Line vs WDV', timeSlot: '9:00 – 10:45 pm', unlockAfter: '10:45 pm', chapter: 'Depreciation', duration: '1h 45m', canJoinNow: true }
        ],
        practiceDpp: { id: 'c11_dpp_1', subject: 'ACCOUNTANCY', teacher: 'CA Rajat Arora Sir', title: 'Bank Reconciliation Statement DPP 03', chapter: 'BRS', duration: '1h' },
        tomorrowRecorded: [
          { subject: 'BUSINESS STUDIES', teacher: 'Disha Khare Ma\'am', dashedClass: 'border-l-[#F97316]', textClass: 'text-[#C2410C]', line: 'Ch 02 : Forms of Business Organisation • Joint Stock...' }
        ],
        tomorrowLive: [
          { time: '4:00 pm', subject: 'ECONOMICS', teacher: 'Love Kaushik Sir', dashedClass: 'border-l-[#10B981]', textClass: 'text-[#059669]', topic: 'Central Tendency...' }
        ],
        questions: [
          { q: '1. Accounting Equation is based on which concept?', options: ['Dual Aspect Concept', 'Going Concern Concept', 'Money Measurement', 'Cost Concept'], ans: 0, chapter: 'Accountancy 11 • Basic Concepts' },
          { q: '2. When Total Utility (TU) is maximum, Marginal Utility (MU) is:', options: ['Positive', 'Negative', 'Zero', 'Maximum'], ans: 2, chapter: 'Microeconomics • Consumer Equilibrium' }
        ]
      },
      science12: {
        id: 'science12',
        shortName: 'Foundati...',
        fullName: 'Parishram / Foundation Science Batch',
        batchCode: 'PW-PARISHRAM-12',
        testTitle: 'Practice Test 04',
        testMeta: 'TEST • 3H • 75 QUESTIONS • 300 MARKS',
        testSyllabus: 'Units, Dimensions and Measurement • Basic Mathematics • Some Basic Principles and Techniques',
        aitsAlert: { title: 'All India Test Series 02 is on Sat, 14 Nov', remaining: 14, total: 30 },
        backlogAlert: { subject: 'Maths', hours: '9h', classesCount: 9 },
        subjects: [
          {
            id: 'phy', name: 'Physics', borderClass: 'border-l-[#0EA5E9]', dashedClass: 'border-l-[#0EA5E9]', textClass: 'text-[#0284C7]', subText: '2 teachers - follow one, or more',
            teachers: [
              { id: 'phy_t1', initial: 'A', name: 'Saleem Sir / Alakh Sir', lectures: 101, dpps: 33, videoHours: 171, chapters: ['Ch 01 : Units, Dimensions and Measurement', 'Ch 02 : Motion in a Straight Line', 'Ch 03 : Motion in a Plane', 'Ch 04 : Laws of Motion', 'Ch 05 : Work, Energy and Power', 'Ch 06 : Electrostatics & Current Electricity'] },
              { id: 'phy_t2', initial: 'R', name: 'Rajwant Sir (RJ Sir)', lectures: 88, dpps: 29, videoHours: 149, chapters: ['Ch 01 : Kinematics', 'Ch 02 : Laws of Motion', 'Ch 03 : Rotational Motion', 'Ch 04 : Electrostatics & Optics'] }
            ]
          },
          {
            id: 'maths_s', name: 'Maths', borderClass: 'border-l-[#10B981]', dashedClass: 'border-l-[#10B981]', textClass: 'text-[#059669]', subText: '1 teacher',
            teachers: [{ id: 'ms_t1', initial: 'B', name: 'Sachin Jakhar Sir', lectures: 95, dpps: 32, videoHours: 160, chapters: ['Ch 01 : Basic Mathematics & Sets', 'Ch 02 : Quadratic Equations', 'Ch 03 : Sequence & Series', 'Ch 04 : Matrices & Determinants', 'Ch 05 : Calculus'] }]
          },
          {
            id: 'org_chem', name: 'Organic Chemistry', borderClass: 'border-l-[#F43F5E]', dashedClass: 'border-l-[#F97316]', textClass: 'text-[#C2410C]', subText: '1 teacher',
            teachers: [{ id: 'oc_t1', initial: 'C', name: 'Pankaj Sijairya Sir / Faisal Sir', lectures: 76, dpps: 28, videoHours: 125, chapters: ['Ch 01 : Some Basic Principles and Techniques', 'Ch 02 : Mole Concept & Limiting Reagent', 'Ch 03 : Hydrocarbons', 'Ch 04 : Haloalkanes & Haloarenes'] }]
          },
          {
            id: 'bio', name: 'Biology', borderClass: 'border-l-[#10B981]', dashedClass: 'border-l-[#10B981]', textClass: 'text-[#059669]', subText: 'Botany • Zoology - choose one or more',
            teachers: [{ id: 'bio_t1', initial: 'R', name: 'Rupesh Sir & Samapti Ma\'am', lectures: 84, dpps: 30, videoHours: 138, chapters: ['Ch 01 : Cell: The Unit of Life', 'Ch 02 : Plant Kingdom', 'Ch 03 : Human Reproduction', 'Ch 04 : Principles of Inheritance & Variation'] }]
          }
        ],
        recordedTasks: [
          { id: 's_rec_1', subject: 'PHYSICS', teacher: 'Saleem Sir', borderClass: 'border-l-[#0EA5E9]', textClass: 'text-[#0284C7]', isOverdue: true, type: 'LECTURE', title: '10 : Motion in a Straight Line (Part 3)', chapter: 'Ch 02 : Motion in a Straight Line', durationSpeed: '1h 37m', duration1x: '2h 25m at 1x', watchedPct: 0, section: 'today' },
          { id: 's_rec_2', subject: 'MATHS', teacher: 'Sachin Jakhar S
