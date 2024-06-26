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
** - target_audience.age_range should be standardized range, and can be comma-separated, like 0-13,13-18,19-59,60+ as we're using in others
* - target_audience.interest ENUMS needs to be defined, or are they mapped to category?
** - Not sure on acceptance_criteria, need to discuss on this 
* - message.catalog.providers.items.media.mimetype is incorrect
* - Is there a need for message.catalog.providers.items.price.maximum_value?
* - What does message.catalog.providers.items.time signify?
** - In ad_specifications, we can only keep SIZE instead of ad_size, FORMAT instead of ad_format. Format should be MIMETYPE.
** - In ad_specifications, we can keep value as only numbers and unit of AD_SIZE_UNIT as KB, MB, GB.
** - In ad_placement, what will be the value of location and location_url?
** - In category_ids, it should be the code that comes, not the actual ID.
*- There's no need to mention fulfillments.state in the catalog.
**- Do we need to mention fulfillments.tags? What is the need?
*- I don't think we need to provide provider.payments here?

Misc:
In the API documentation, tags are defined within ENUMS              

** - In ad_specifications, we can keep value as only numbers and unit of AD_SIZE_UNIT as KB, MB, GB.
** - In ad_placement, what will be the value of location and location_url?
** - In category_ids, it should be the code that comes, not the actual ID.
**- Do we need to mention fulfillments.tags? What is the need?
** - Not sure on acceptance_criteria, need to discuss on this 
** - target_audience.age_range should be standardized range, and can be comma-separated, like 0-13,13-18,19-59,60+ as we're using in others
