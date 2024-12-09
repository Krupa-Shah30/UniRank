
# UniRank Project

## Overview
UniRank is a consulting firm specializing in analyzing and improving university rankings. This project focuses on creating a comprehensive database system to support stakeholders at the University of Maryland's (UMD) Smith School of Business. The project integrates data from multiple sources and years to provide insights into university and program rankings, competitor analysis, and evaluation criteria.

## Project Mission
The mission of this project is to empower UMD Smith School stakeholders by:
- Providing detailed and accurate ranking data.
- Developing a state-of-the-art database that consolidates diverse data over multiple years.
- Analyzing how ranking sources evaluate programs based on specific criteria.
- Identifying top competitors and strategizing ways to improve UMD's market standing.

## Database Design
The database is designed to store and analyze ranking data comprehensively. It includes the following tables:

### Tables
1. **University**: Stores university details like name, location, founding year, and alumni network size.
2. **Program**: Contains program-specific details such as tuition fees, duration, employability rate, and associated university.
3. **RankSource**: Maintains information about ranking sources, including their names and links.
4. **Criteria**: Lists evaluation criteria used by ranking sources.
5. **Ranks**: Stores ranking data for programs across different years and sources.
6. **User**: Captures user information such as name, email, category (e.g., student, advisor).

### Relationships
- Programs are linked to Universities.
- Rankings are tied to Programs and RankSources.
- Criteria are associated with RankSources.

## Data Sources
The project uses renowned ranking platforms for data collection:
- QS World University Rankings
- Edvoy
- Poets & Quants
- Fortune
- U.S. News & World Report
- Financial Times

These sources provide a multifaceted view of academic institutions based on criteria such as academic reputation, alumni outcomes, career progress, and financial resources.

## Ranking Criteria
The rankings are based on a comprehensive set of criteria:
- Academic Reputation
- Faculty-to-Student Ratio
- Employer Reputation
- Alumni Salary
- Career Outcomes
- Graduation Rate
- Return on Investment (ROI)
- Employment Rate

This approach ensures a balanced analysis of both academic excellence and post-graduation success.

## Key Features
1. **Historical Trends**: Analyze ranking trends for UMD programs like Information Systems and Business Analytics over the past three years.
2. **Competitor Analysis**: Identify top competitors for UMD's MBA program based on recent rankings.
3. **Evaluation Insights**: Understand how different sources weigh criteria in their evaluations.

## Views for Analysis
### Example Views:
1. **UMD Program Rankings**:
   ```sql
   SELECT * FROM [UniRank.ViewProgramRankings] ORDER BY rankYear DESC, progId;
   ```
2. **Ranking Sources Used**:
   ```sql
   SELECT * FROM [UniRank.ViewRankSources];
   ```
3. **Ranking Trends for Information Systems and Business Analytics**:
   ```sql
   SELECT * FROM [UniRank.ViewISBAUMDRank] ORDER BY progName, rankYear DESC;
   ```
4. **Top Competitors for MBA**:
   ```sql
   SELECT DISTINCT tc.uniName, tc.rankNumber, rs.rankSrcName 
   FROM [UniRank.TopCompetitorsMBA] tc 
   INNER JOIN [UniRank.RankSource] rs ON rs.rankSrcId = tc.rankSrcId 
   ORDER BY tc.rankNumber ASC;
   ```

## Significance
This project provides actionable insights for UMD stakeholders to enhance their programs' visibility and competitiveness in the academic landscape.

## How to Use the Database
1. Use the following command to select the database:
   ```sql
   USE BUDT702_Project_0501_07;
   ```
2. Execute the provided SQL queries under each view to analyze specific questions related to rankings.

## Conclusion
The UniRank project delivers a robust platform for analyzing university rankings by integrating diverse data sources and employing comprehensive evaluation criteria. It empowers stakeholders with insights into historical trends, competitor standings, and evaluation methodologies to make informed decisions for strategic improvements.
