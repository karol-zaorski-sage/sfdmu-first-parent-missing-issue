# Missing lookup values for children records

## Prerequisite

- Account.csv with 1 record
  - Name = "Sample Account for Entitlements"
- Opportunity.csv with 2 records:
  - first record - Account.Name = ""
  - second record - Account.Name = "Sample Account for Entitlements"

## Steps

- run command `sfdx sfdmu:run --targetusername sfdmu --sourceusername csvfile -p data`

## Expected results

- Records are upserted with the correct values

## Actuall results

- Both Opportunities don't have Account relationshipo


## Notes

When the FIRST RECORD of the Opportunity.csv file has Account.Name = "Sample Account for Entitlements", than script is working correctly.
