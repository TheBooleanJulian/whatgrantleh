# Requirements Document

## 1. Application Overview

### 1.1 Application Name\nSGGrantLeh

### 1.2 Application Description

SGGrantLeh is a web application designed to help Singapore entrepreneurs, SME owners, and startup founders discover and qualify for relevant government grants. The platform matches user business profiles against a comprehensive database of Singapore government grants, providing personalized recommendations with AI-powered justifications to help users confidently identify funding opportunities for growth, expansion, and digital transformation.

## 2. Users and Usage Scenarios

### 2.1 Target Users

- Singapore entrepreneurs
- SME owners\n- Startup founders who are uncertain about grant eligibility

### 2.2 Core Usage Scenarios

- Business owners seeking government funding for expansion projects
- Entrepreneurs exploring grants for digital transformation initiatives
- SME founders looking to understand which grants match their business profile and goals

## 3. Page Structure and Functional Description\n

### 3.1 Page Structure

```
SGGrantLeh Application
├── Home Page (Hero Section)\n├── Dashboard (Results Page)\n├── Grant Detail Modal
├── Disclaimer Page
├── Terms of Use Page
└── Privacy Policy Page
```\n
### 3.2 Home Page (Hero Section)
\n#### 3.2.1 Visual Design
- Background: Crisp White
- Primary color: Enterprise Blue (#0033A0)
- Accent color: Red (#ED2939) for primary action buttons
- Professional, Enterprise-grade design inspired by GovTech Singapore

#### 3.2.2 Content Elements
- Headline: Stop Leaving Government Grants on the Table\n- Subheadline: Find and qualify for the right Singapore grants to fund your growth, expansion, and digital transformation.

#### 3.2.3 Input Component
Dual-input options:\n- Option 1: Text area with title Describe your business and projects in 3 sentences
- Option 2: Input field with label Enter your Business Website URL (We will scrape for you)

#### 3.2.4 CTA Button
- Label: What SG Grant can I apply leh?
- Style: Bold red button (#ED2939)
- Action: Submit user input and navigate to Dashboard

### 3.3 Dashboard (Results Page)\n
#### 3.3.1 Loading State
- Display animated loading indicator
- Show rotating text: Cross-referencing [agency] databases...
- Agency names cycle through: Enterprise Singapore, IMDA, SSG, WSG, etc.

#### 3.3.2 Top Recommended Matches Section
- Display top 6 most relevant grants\n- Layout: 3-column grid
- Visual highlight: Orange/gold border on cards
\n#### 3.3.3 Other Eligible Grants Section\n- Display remaining matched grants
- Layout: 3-column grid
- Sorting: By grant size (descending)

#### 3.3.4 Grant Match Card Design
Each card displays:
- Grant Name\n- Governing Agency
- Max Grant Size
- 1-sentence description
- Clickable to open detail view
\n### 3.4 Grant Detail Modal

#### 3.4.1 Modal Trigger
- Opens when user clicks any Grant Match Card
- Freezes background screen

#### 3.4.2 Information Display
Display the following information in order:
- Agency
- Grant Type
- Funding Amount / % Support
- Last Updated timestamp
- AI Match Justification (in purple-blue AI-themed rounded rectangle)
- Supported Use Cases
- Eligibility Criteria
- Application Process Timeline (displayed as visual timeline infographic)
- Required Documents
- Restrictions/Notes
\n#### 3.4.3 AI Match Justification Section\n- Visual treatment: Purple-blue AI-themed rounded rectangle background
- Clear indication that content is AI-generated and personalized
- Content structure: 3 paragraphs (see Business Rules section)
\n#### 3.4.4 Application Process Timeline Infographic
- Display as horizontal timeline visualization
- Each timeline node includes:
  - Step number
  - Step title
  - Brief description
  - Estimated duration or deadline
- Visual design elements:
  - Connected nodes with arrows
  - Clear progression indicators
  - Color-coded stages (e.g., preparation, submission, review, approval)

#### 3.4.5 Primary Action Button
- Label: Go to Official Application Page
- Style: Screen-frozen button
- Action: Opens official government portal link in new tab

### 3.5 Footer (All Pages)

#### 3.5.1 Navigation Links
- Disclaimer (links to Disclaimer Page)
- Terms of Use (links to Terms of Use Page)
- Privacy Policy (links to Privacy Policy Page)

#### 3.5.2 Attribution
- Text: Built by TheBooleanJulian

### 3.6 Disclaimer Page
- Standalone page with disclaimer content

### 3.7 Terms of Use Page
- Standalone page with terms of use content

### 3.8 Privacy Policy Page
- Standalone page with privacy policy content

## 4. Business Rules and Logic

### 4.1 User Input Processing

#### 4.1.1 Text Input Processing
- Accept user-provided business description (prompt users for at least 3 sentences)\n- Extract key information: Industry, Business stage, Goals, Project type\n
#### 4.1.2 URL Input Processing
- Accept business website URL
- Scrape website content
- Extract key information: Industry, Business stage, Goals, Project type
\n### 4.2 Grant Database Structure

Each grant record contains:
- Grant Name
- Agency
- Grant Type (e.g. PSG, EDG, MRA)
- Description (clear and concise)\n- Funding Amount / % Support
- Eligibility Criteria
- Supported Use Cases (e.g. digital transformation, hiring, overseas expansion)
- Application Process (steps and timeline)
- Required Documents
- Restrictions / Notes
- Official Application Link
- Last Updated Timestamp
\n### 4.3 Data Source Restrictions

Grant data must be sourced exclusively from:
- https://www.enterprisesg.gov.sg/
- https://www.apply.gov.sg/grants/business
- https://grants.gobusiness.gov.sg/
- https://www.ssg.gov.sg/
- https://www.imda.gov.sg/
- https://www.startupsg.gov.sg/
- https://www.wsg.gov.sg/

### 4.4 Grant Matching Logic\n
#### 4.4.1 Matching Criteria\n- Eligibility rules alignment\n- Use-case alignment with user goals
- Restriction compliance\n
#### 4.4.2 Ranking Algorithm
- Calculate relevance score for each grant
- Rank results by relevance score (descending)
- Top 6 results designated as Top Recommended Matches
- Remaining results sorted by grant size

### 4.5 AI Match Justification Generation

#### 4.5.1 Content Structure
Exactly 3 paragraphs:\n- Paragraph 1: The Business Innovation (Why the startup's model qualifies)
- Paragraph 2: Market Viability in Singapore (How it impacts the local economy)\n- Paragraph 3: Scalability (Exactly how the specific grant funds will be utilized for scaling)\n
#### 4.5.2 Tone and Language\n- Highly corporate and persuasive
- Use standard Singapore government phrasing: capability upgrading, digital transformation, market readiness
- Concise, professional, and persuasive
- Avoid hype or fluff
\n### 4.6 Application Process Timeline Generation

#### 4.6.1 Timeline Data Structure
- Extract application process steps from grant database
- Structure each step with: Step number, Title, Description, Duration/Deadline
\n#### 4.6.2 Timeline Visualization Rules
- Display steps in chronological order
- Use visual connectors between steps
- Highlight current or upcoming steps if applicable
- Ensure timeline is responsive and readable on all devices

### 4.7 Data Validation Rules
- No hallucinated data permitted
- Only verified, source-linked information
- Regular data refresh (daily sync recommended)
\n## 5. Exception and Boundary Cases

| Scenario | Handling |
|----------|----------|
| User submits empty input | Display validation message: Please provide business description or website URL |
| Website URL scraping fails | Display error message: Unable to access website. Please try text description instead |
| No matching grants found | Display message: No grants match your current profile. Consider refining your business description |
| Grant database unavailable | Display error message: Service temporarily unavailable. Please try again later |\n| External government portal link broken | Display warning in modal: Official link may be outdated. Last verified: [timestamp] |
| User clicks CTA during loading | Disable button during processing to prevent duplicate submissions |\n| Application process timeline data incomplete | Display available steps with note: Complete timeline available on official portal |

## 6. Acceptance Criteria

1. Home Page displays Hero Section with headline, subheadline, dual-input component, and red CTA button
2. User can input business description via text area OR website URL
3. Clicking CTA button triggers loading state with rotating agency names
4. Dashboard displays Top Recommended Matches (top 6) with orange/gold border in 3-column grid
5. Dashboard displays Other Eligible Grants sorted by grant size in 3-column grid
6. Each Grant Match Card shows Grant Name, Agency, Max Grant Size, and 1-sentence description
7. Clicking any card opens Grant Detail Modal with all specified information fields
8. AI Match Justification appears in purple-blue rounded rectangle with 3-paragraph structure
9. Application Process Timeline displays as clear visual infographic with connected steps, descriptions, and durations
10. Timeline infographic is responsive and readable across devices
11. Go to Official Application Page button opens government portal in new tab
12. Footer displays links to Disclaimer, Terms of Use, Privacy Policy, and Built by TheBooleanJulian attribution
13. Grant data is sourced only from specified Singapore government domains\n14. Grant matching uses eligibility rules, use-case alignment, and restrictions
15. Results are ranked by relevance score
16. All UI elements follow GovTech Singapore design: White background, Enterprise Blue (#0033A0), Red accents (#ED2939)
17. Application is responsive across desktop and mobile devices

## 7. Out of Scope for This Release

1. User account creation and login functionality
2. Saving or bookmarking favorite grants
3. Application form pre-filling or submission through the platform
4. Email notifications for new matching grants
5. Comparison tool for multiple grants side-by-side\n6. Grant application status tracking\n7. Multi-language support beyond English
8. Integration with government application portals for direct submission
9. Historical data or trends on grant approval rates
10. Community features such as user reviews or success stories
```
