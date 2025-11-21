# Contract Supplier 1:1 

The API Endpoint `/api/v1/org/contracts/suppliers_11` is a very special API endpoint. 

The data model of ZEIT.IO is very flexible. By default, a project can have multiple members. 
Each project member is connected with the project through a `member` entity and a `contract`. 
But many head hunter agencies don't need this flexibility. 
Most of the time they only 1 member attached to a project. 
To simplify the creation process, we build a special form in the UI, for exactly this use case. 
After submitting that form, a `contract` and a `project` is created and they are linked to each other. 
A project created by this form can not have multiple members. 
These kind of projects always have exactly one member. 

Here are the fileds for the payload: 

| **Field Name**                      | **Example Value**           | **Description**                                                                                                                                                        | **Mandatory** |
|-------------------------------------|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| "currency"                          | "EUR"                       | The selected currency ISO-Code. The default value is `EUR`.                                                                                                            | NO            |
| "cntr_title"                        | "OKR Expert"                | Title of the contract. Usually the job title. For example `Senior GoLang Engineer`.                                                                                    | YES           |
| "cntr_content"                      | "lorem ipsum"               | The full content of the contract. Can be empty.                                                                                                                        | NO            |
| "cntr_recipient_email"              | "z_worker@zeit.io"          | Email of the freelancer who should receive the contract.                                                                                                               | YES           |  
| "cntr_recipient_locale"             | "de"                        | The language of the recipient. Default is `de`.                                                                                                                        | YES           | 
| "cntr_recipient_firstname"          | "Max"                       | Firstname of the recipient supplier.                                                                                                                                   | YES           |
| "cntr_recipient_lastname"           | "Mustermann"                | Lastname of the recipient supplier.                                                                                                                                    | YES           |
| "cntr_recipient_message"            | "as discussed on the phone" | Message to the recipient supplier.                                                                                                                                     | NO            |
| "cntr_compensation_type"            | "hourly"                    | Must be one of [`hourly`, `hourly_multi`, `daily`, `daily_multi`].                                                                                                     | YES           | 
| "cntr_hourly_wage"                  | 9900                        | The hourly rate for the freelancer/supplier. In this case 99 EUR.                                                                                                      | NO            |
| "cntr_billing_rate"                 | 11500                       | What we bill the customer. In this case 115 EUR. Not visible to the freelancer/supplier.                                                                               | NO            |
| "cntr_hourly_wage_remote"           | 0                           | Hourly remote rate for the freelancer.                                                                                                                                 | NO            |
| "cntr_billing_rate_remote"          | 0                           | What we bill the customer for remote hours. Not visible to the freelancer/supplier.                                                                                    | NO            |
| "cntr_hourly_wage_on_site_1"        | 0                           | Hourly wage for onsite-1 hours for the freelancer.                                                                                                                     | NO            |
| "cntr_billing_rate_on_site_1"       | 0                           | What we bill the customer for onsite-1 hours. Not visible to the freelancer/supplier.                                                                                  | NO            |
| "cntr_hourly_wage_on_site_2"        | 0                           | Hourly wage for onsite-2 hours for the freelancer.                                                                                                                     | NO            |
| "cntr_billing_rate_on_site_2"       | 0                           | What we bill the customer for onsite-2 hours. Not visible to the freelancer/supplier.                                                                                  | NO            |
| "cntr_hourly_wage_travel"           | 0                           | Hourly wage for travel hours for the freelancer.                                                                                                                       | NO            |
| "cntr_billing_rate_travel"          | 0                           | What we bill the customer for travel hours. Not visible to the freelancer/supplier.                                                                                    | NO            |
| "cntr_daily_wage"                   | 0                           | Daily wage for the freelancer.                                                                                                                                         | NO            |
| "cntr_daily_billing_rate"           | 0                           | Daily rate we bill the customer. Not visible to the freelancer/supplier.                                                                                               | NO            |
| "cntr_daily_wage_remote"            | 0                           | Daily wage for remote work for the freelancer.                                                                                                                         | NO            |
| "cntr_daily_billing_rate_remote"    | 0                           | Daily rate for remote we bill the customer. Not visible to the freelancer/supplier.                                                                                    | NO            |
| "cntr_daily_wage_on_site_1"         | 0                           | Daily wage for onsite work for the freelancer.                                                                                                                         | NO            |
| "cntr_daily_billing_rate_on_site_1" | 0                           | Daily rate for onsite we bill the customer. Not visible to the freelancer/supplier.                                                                                    | NO            |
| "cntr_payment_term"                 | "30"                        | Payment term in days we agreed with the supplier/freelancer. If not present, the configured orga default value is used.                                                | NO            |
| "cntr_skonto1_target"               | 14                          | Skonto 1 target in days. If not present, the configured orga default value is used.                                                                                    | NO            |
| "cntr_skonto1_discount"             | 150                         | Skonto 1 discount in %. 150 is equal to 1,5%. If not present, the configured orga default value is used.                                                               | NO            |
| "cntr_skonto2_target"               | 7                           | Skonto 2 target in days. If not present, the configured orga default value is used.                                                                                    | NO            |
| "cntr_skonto2_discount"             | 300                         | Skonto 2 discount in %. 150 is equal to 1,5%. If not present, the configured orga default value is used.                                                               | NO            |
| "cntr_skonto3_target"               | 0                           | Skonto 3 target in days. If not present, the configured orga default value is used.                                                                                    | NO            |
| "cntr_skonto3_discount"             | 0                           | Skonto 3 discount in %. 150 is equal to 1,5%. If not present, the configured orga default value is used.                                                               | NO            |
| "cntr_membership_offset"            | 5                           | Membership offset in days. Controls how many days after project end the supplier has access to the project. If not present, the configured orga default value is used. | NO            |
| "cntr_credit_note_procedure"        | true                        | Does the supplier use the credit note procedure? For approved timesheets a credit note will be issued. If not present, the configured orga default value is used.      | NO            |
| "cntr_needs_approval"               | true                        | Controls whether booked times need an approval or not. If not present, the configured orga default value is used.                                                      | NO            |
| "cntr_needs_signed_proof"           | false                       | Is a signed PDF uplaod needed, in addition to the recorded TimeRecords? Usually not needed. If not present, the configured orga default value is used.                 | NO            |
| "cntr_role_activity_admin"          | false                       | Does the supplier has permission to create new activities in the project? Usually not needed. If not present, the configured orga default value is used.               | NO            |
| "cntr_send_offer_email"             | false                       | Should the offer email send out after successfully creation? Default value is false.                                                                                   | NO            |
| "proj_name"                         | "OKR Coaching"              | The name of the project used on outgoing invoices. Usually provided by the customer.                                                                                   | YES           |
| "proj_identifier"                   | "OKR Coaching HKL-1"        | Identifier can be same as name, but must be unique in the organisation. This value is used in the UI to identify the project.                                          | YES           |
| "proj_description"                  | "Best OKR coaching in town" | The project description. Visible to all members and approvers.                                                                                                         | NO            |
| "proj_start_date"                   | "2025-09-01"                | Start date of the project. TimeRecords must be within project start and end.                                                                                           | YES           |
| "proj_end_date"                     | "2025-12-31"                | End date of the project. TimeRecords must be within project start and end.                                                                                             | YES           |
| "proj_project_no"                   | "P-444"                     | Project number. Depending on the orga config, this value might be mandatory and might be seeded by ZEIT.iO.                                                            | NO            |
| "proj_order_no"                     | "PO-4994"                   | An order number. Usually provided by the customer. Depending on the orga config this value can be mandatory.                                                           | NO            |
| "proj_interval"                     | 0                           | Interval for time tracking in minutes. If greater 0 all TimeRecords are rounded up to that interval.                                                                   | NO            |
| "proj_customer_id"                  | ""                          | The customer ID. References a customer in ZEIT.IO.                                                                                                                     | NO            |
| "proj_customer_department_id"       | ""                          | The customer department ID. References a customer department in ZEIT.IO.                                                                                               | NO            |
| "proj_customer_contact_person_id"   | ""                          | The customer contact-person ID. References a customer contact-persoon in ZEIT.IO.                                                                                      | NO            |
| "proj_contact_person"               | "Mariane Musterfrau"        | A contact person for the supplier/freelancer.                                                                                                                          | NO            |
| "proj_contact_person_email"         | "m.musterfrau@zeit.io"      | Contact person email for the supplier/freelancer.                                                                                                                      | NO            |
| "proj_budget_type"                  | "default"                   | The budget type of the project. Must be one of: [`default`, `days`].                                                                                                   | NO            |
| "proj_hour_budget"                  | 500                         | The hour budget. How many hours max can be booked on this project? If `proj_budget_type` is `default` then this value is mandatory.                                    | YES           |
| "proj_hour_budget_wage"             | 11500                       | The average billing rate per hour we bill to the customer.                                                                                                             | NO            |
| "proj_day_budget"                   | 0                           | The day budget. In case budget type is `days`. How many days max ca be booked on this project? If `proj_budget_type` is `days` then this value is mandatory.           | NO            |
| "proj_day_budget_rate"              | 0                           | The average billing rate per day we bill to the customer.                                                                                                              | NO            |
| "proj_budget"                       | 5750000                     | Currency budget for time tracking.In this example `57.500,00` EUR.                                                                                                     | YES           |
| "proj_budget_expenses"              | 0                           | Currency budget for expenses.                                                                                                                                          | NO            |
| "proj_can_be_overbooked"            | false                       | Controls whether the project can be overbooked or not. Default is false.                                                                                               | NO            |


## Example 1 

Here is an example payload for

 - Project budget type: hourly 
 - Project hour budget: 500 hours 
 - Project currency budget: 57.500,00 EUR
 - Contract compensation type: hourly 
 - Contract purchase rate: 99 EUR / hour 
 - Contract sell rate: 115 EUR / hour
 - Contract status: Draft. The invite email is not sent out. 

```json
{
  "currency": "EUR",
  "cntr_title": "OKR Coaching",
  "cntr_content": "contract content",
  "cntr_recipient_email": "z_worker@test.io",
  "cntr_recipient_locale": "de",
  "cntr_recipient_firstname": "Max",
  "cntr_recipient_lastname": "Mustermann",
  "cntr_recipient_message": "",
  "cntr_compensation_type": "hourly",
  "cntr_hourly_wage": 9900,
  "cntr_billing_rate": 11500,
  "cntr_hourly_wage_remote": 0,
  "cntr_billing_rate_remote": 0,
  "cntr_hourly_wage_on_site_1": 0,
  "cntr_billing_rate_on_site_1": 0,
  "cntr_hourly_wage_on_site_2": 0,
  "cntr_billing_rate_on_site_2": 0,
  "cntr_hourly_wage_travel": 0,
  "cntr_billing_rate_travel": 0,
  "cntr_daily_wage": 0,
  "cntr_daily_billing_rate": 0,
  "cntr_daily_wage_remote": 0,
  "cntr_daily_billing_rate_remote": 0,
  "cntr_daily_wage_on_site_1": 0,
  "cntr_daily_billing_rate_on_site_1": 0,
  "cntr_payment_term": "30",
  "cntr_skonto1_target": 0,
  "cntr_skonto1_discount": 0,
  "cntr_skonto2_target": 0,
  "cntr_skonto2_discount": 0,
  "cntr_skonto3_target": 0,
  "cntr_skonto3_discount": 0,
  "cntr_credit_note_procedure": true,
  "cntr_needs_approval": true,
  "cntr_needs_signed_proof": false,
  "cntr_role_activity_admin": false,
  "cntr_membership_offset": 0,
  "cntr_send_offer_email": false,
  "proj_name": "OKR Coaching",
  "proj_identifier": "OKR Coaching 1",
  "proj_description": "Best OKR coaching in town!",
  "proj_start_date": "2025-09-01",
  "proj_end_date": "2025-12-31",
  "proj_project_no": "PO-4i44",
  "proj_order_no": "B-4994",
  "proj_interval": 0,
  "proj_customer_id": "",
  "proj_customer_department_id": "",
  "proj_customer_contact_person_id": "",
  "proj_contact_person": "Robert Reiz",
  "proj_contact_person_email": "reiz@test.io",
  "proj_budget_type": "default",
  "proj_hour_budget": 500,
  "proj_hour_budget_wage": 11500,
  "proj_day_budget": 0,
  "proj_day_budget_rate": 0,
  "proj_budget": 5750000,
  "proj_budget_expenses": 0,
  "proj_can_be_overbooked": false
}
```
