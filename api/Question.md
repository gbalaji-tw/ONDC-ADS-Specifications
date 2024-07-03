## Question #
Fulfillment states?
Order states?
Payment states?

How is tracking communicated?
say "Payment type - post fulfillment"
how to share the actual cpm vs expected cpm?

chat link for neog  - seller link(BPP)
on_search -> message.provider - >descriptor.additional_desc.url

post:
/init

Enums for addons?
    - creative Generation - chat link with creator
        price
        tax
        terms
    - managed campaign - chat link with creator
        price
        tax
        terms

Offers?
    discount amt



10 CPM over 1 week

days/weeks? - use start date
item - tags - start_date, end_date.
pricing based on promise sorted by seller conditions

          time:
            label: validity
            range:
              start: '2022-12-24T00:00:00.000Z'
              end: '2022-12-31T00:00:00.000Z'



ADS Based Feedback

/search
*- context.version 1.0.0 is wrong, it should be 2.0.0
*- BAP_TERMS needs to be there as a tag group for finer fees
*- buyer_id can be written as BUYER_DETAILS and inside of this, we can define GST or other details

/on_search
* - context.version should be 2.0.0
* - message.catalog.fulfillments should define both ONLINE and OFFLINE as example
* - message.catalog.payments should not have "collected_by" attribute
* - message.catalog.providers.locations should have gps and address
* - message.catalog.providers.locations.tags serviceability should have category, val and unit
* - seller_id can be changed to SELLER_DETAILS
* - target_audience.age_range should be standardized range, and can be comma-separated, like 0-13,13-18,19-59,60+ as we're using in others
* - target_audience.interest ENUMS needs to be defined, or are they mapped to category?
** - Not sure on acceptance_criteria, need to discuss on this 
* - message.catalog.providers.items.media.mimetype is incorrect
* - Is there a need for message.catalog.providers.items.price.maximum_value?
* - What does message.catalog.providers.items.time signify?
* - In ad_specifications, we can only keep SIZE instead of ad_size, FORMAT instead of ad_format. Format should be MIMETYPE.
* - In ad_specifications, we can keep value as only numbers and unit of AD_SIZE_UNIT as KB, MB, GB.
* - In ad_placement, what will be the value of location and location_url?
** - In category_ids, it should be the code that comes, not the actual ID.
*- There's no need to mention fulfillments.state in the catalog.
*- Do we need to mention fulfillments.tags? What is the need?
*- I don't think we need to provide provider.payments here?

Misc:
In the API documentation, tags are defined within ENUMS              

** - In category_ids, it should be the code that comes, not the actual ID.
** - target_audience.age_range should be standardized range, and can be comma-separated, like 0-13,13-18,19-59,60+ as we're using in others


Policies should go under BPP Terms in /on_init instead
** No need to define categories that are already in the taxonomy

/on_search
* providers.tags has category listed as SRV11-*, it should be ADS10
There is no parent_item_id PI1 defined, please remove the key
* item.price.value and item.price.offered_value should be the same to avoid confusion. You can instead define the maximum price.
*What does quantity.count and quantity.measure.value describe exactly?
item.tags.description is null, please remove they key
** No need to define categories that are already in the taxonomy
There should be no need of provider.fulfillments at this level and should be part of the /select and /on_select call, as we're already describing the location for the ad placement before.

/select
Context.version should be 2.0.0
message.order.items.id should be I1 rather than the name of the item
items.add-ons id is not matching with /on_search
In fulfilments, there are two objects. We don't need to mention ID for the fulfillment here, only the type suffice.

/on_select
context.version should be 2.0.0
order.provider.id is not correct according to previous calls
fulfillment_ids was not present in /select and the ID is incorrect
fulfillments.ids is not "ONLINE", it should be type. ID should be alphanumeric unique identifier.
quote.breakup.title "Ads" is not an item in the catalog
There is no item with a value of INR 500 in the catalog
quote.breakup.item.id "PI1" is incorrect
Selected item is I1, how are we applying tax to I2?
There was no offer in catalog, how are we applying offer coupon for discount?
Creative generation add on price id is incorrect

/init
context.version should be 2.0.0
** What will be described in "ITEM_REQ" in "BUYER_TERMS"

/on_init
context.version should be 2.0.0
quantity.selected does not match the previous calls
Mostly same as /on_select and new tag groups are defined which were not present before, what is the need of them?
payments.params.amount is incorrect and does not match quote




- descriptor:
            code: acceptance_criteria
          list:
          - descriptor:
              code: allowed_policies
            value: 'ONDC Seller nodes & seller apps only'


        fulfillments:
         - id: 
           type: ONLINE
           tags:
            - descriptor:
              code: location
              list:
              - descriptor:
                  code: location_url
                  value: ''
              - descriptor:
                  code: lat
                  value: ''
              - descriptor:
                  code: long
                  value: ''

Allowed Domains: Enumize it.


Retail
Logistics
Grocery
F&B
Fashion
Electronics
Home & Decor
Pharma
Health & Wellness
Pharma
Autoparts & Components
Building and construction supplies
Chemicals



  [
        {
          "code":"bpp_terms",
          "list":
          [
            {
              "code":"max_liability",
              "value":"2"
            },
            {
              "code":"max_liability_cap",
              "value":"10000.00"
            },
            {
              "code":"mandatory_arbitration",
              "value":"false"
            },
            {
              "code":"court_jurisdiction",
              "value":"Bengaluru"
            },
            {
              "code":"delay_interest",
              "value":"7.50"
            },
            {
              "code":"tax_number",
              "value":"gst_number_of_sellerNP"
            },



1. Update Target audience
2. Update Flow UI
3. Update BPP Terms
4. Checking to ONDC repo.



