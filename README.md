# South Korean National Assembly legislative data for politopic.net

- Note that [politopic.net](https://politopic.net) is still under construction, and the naming conventions and variables may change frequently.
- The current legislative session is 21, for the years 2020-2024. Data on the previous session, 20, is incomplete as much of it has been removed from the National Assembly website.

### Scraped data
The following data is scraped from the [National Assembly website](https://likms.assembly.go.kr/bill/main.do); see [y-wenl/SKNADataScraper](https://github.com/y-wenl/SKNADataScraper).
- The current members of the National Assembly and their information.
    - `member_list_data_session21.json`, a simple list of member names and corresponding ID numbers.
    - `member_info_data_session21.json`, a list containing detailed information on each member.
- A list of all bills voted on in the each session.
    - `bill_list_data_session21.json`, raw output from the National Assembly website AJAX request. The key variable is `resListVo`, which contains a list of every bill, including the bill name and ID numbers.
- Detailed information on each bill in the list.
    - `bills/` directory containing a JSON file for each bill. Each JSON file includes not only the bill name and ID numbers, but also the relevant committee and a list of ever assembly member's vote on the bill.

### Manually collected data
The following data was collected by hand.
- `manual_member_info.yaml`, a general list of data for each member which will add to or overwrite data in `member_info_data_session21`. This is currently used only to set the gender of each member and to correct some romanized names (specifically, to add a space between surname and given name).
- `member_replacements.yaml`, a list of members who left or joined the assembly during the session.

### Processed data
The following data supplements the scraped and collected data with additional processing or analysis; see [y-wenl/SKNA_Analysis](https://github.com/y-wenl/SKNA_Analysis).
- A list of all bills voted on in each session
    - `processed/bill_data_session21.json`, which contains a list of every bill, including the bill name, ID numbers, vote result, and other data. This is a cleaned-up version of `bill_list_data_session21.json`.
- Each assembly member's vote on each bill
    - `processed/member_vote_data_session21.csv`. Columns list members (by ID) and rows bills. 1 = vote in favor, -1 = vote against, 0 = abstention, empty = no vote.
- The committee of each bill
    - `processed/committee_bill_data_session21.csv`. Columns list committees and rows bills. 1 = bill is in the committee, 0 = bill not in the committee.
- A list of data on each member, consisting of unprocessed data like name, district, and ID, as well as member-specific processed data: attendance rate, absentee rate, frequency of voting with the majority party (더불어민주당), vote alignment with the 3 largest parties (더불어민주당, 국민의힘, 정의당), and loyalty to their own party.
    - `processed/members_fullinfo_session21.json`
    - `webdata/members_fullinfo_session21.csv`
- A similar list of data on each member, organized in the data format expected by [DataTables](https://datatables.net) for display on [politopic.net](https://politopic.net).
    - `webdata/members_data_session21.json`
- For each member, a JSON file listing that member's vote on each bill, as well as their party's vote and the overall bill result. The data format is that expected by [DataTables](https://datatables.net) for display on [politopic.net](https://politopic.net).
    - `webdata/members/`
