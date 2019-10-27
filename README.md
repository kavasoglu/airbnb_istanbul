# Airbnb Istanbul Data Playbook

Airbnb is an online marketplace to arrange or offer places to stay for a short term. Airbnb has mainly 2 customer profiles: the people who wants to stay in a place for a short time and the people who offers places to stay.

## Project Definition

In this project, we are going to focus on problems of the people who offers places to stay. One of the main problems of these people is that it is very difficult to decide price for a new place because Airbnb does not provide a guidance how to choose relevant price for a place and there is a high competition on the online marketplace. If you set up the price to a high value, then you might miss your potential customers, and if the otherwise happens then you are going to make less profit than you are actually able to do. And, this problem can be solved by the help of machine learning algorithms.

In this project, we are going to analyze Istanbul data to look at this problem and answer some of the questions we have. You can find detailed explanations in the notebook.  

## Data Source

We get the publicly available data from [InsideAirbnb](http://insideairbnb.com/get-the-data.html). To check Istanbul map visualization check [here](http://insideairbnb.com/istanbul/?neighbourhood=&filterEntireHomes=false&filterHighlyAvailable=false&filterRecentReviews=false&filterMultiListings=false)

## Project Structure

Data is located under *istanbul* folder which was published on 29 June, 2019. In this folder, there are many datasets, but for the explained problem above we are just going to use *listings* data.    

**listings.csv:** (19727 rows & 105 columns)   
id,listing_url,scrape_id,last_scraped,name,summary,space,description,experiences_offered,neighborhood_overview,  
notes,transit,access,interaction,house_rules,thumbnail_url,medium_url,picture_url,xl_picture_url,host_id,host_url,  
host_name,host_since,host_location,host_about,host_response_time,host_response_rate,host_acceptance_rate,  
host_is_superhost,host_thumbnail_url,host_picture_url,host_neighbourhood,host_listings_count,  
host_total_listings_count,host_verifications,host_has_profile_pic,host_identity_verified,street,neighbourhood,  
neighbourhood_cleansed,neighbourhood_group_cleansed,city,state,zipcode,market,smart_location,country_code,country,  
latitude,longitude,is_location_exact,property_type,room_type,accommodates,bathrooms,bedrooms,beds,bed_type,  
amenities,square_feet,price,weekly_price,monthly_price,security_deposit,cleaning_fee,guests_included,extra_people,  
minimum_nights,maximum_nights,minimum_minimum_nights,maximum_minimum_nights,minimum_maximum_nights,  
maximum_maximum_nights,minimum_nights_avg_ntm,maximum_nights_avg_ntm,calendar_updated,has_availability,  
availability_30,availability_60,availability_90,availability_365,calendar_last_scraped,number_of_reviews,  
number_of_reviews_ltm,first_review,last_review,review_scores_rating,review_scores_accuracy,review_scores_cleanliness,  
review_scores_checkin,review_scores_communication,review_scores_location,review_scores_value,requires_license,  
license,jurisdiction_names,instant_bookable,is_business_travel_ready,cancellation_policy,  
require_guest_profile_picture,require_guest_phone_verification,calculated_host_listings_count,  
calculated_host_listings_count_entire_homes,calculated_host_listings_count_private_rooms,  
calculated_host_listings_count_shared_rooms,reviews_per_month  

105 columns need a handful data processing operations, and you can find the operations implemented in the notebook.

## Requirements & How to Run

Must be installed:
- Python 3
- Jupyter notebook  
Run `jupyter notebook` in the project folder to access *airbnb_istanbul.ipynb* on your web browser, then execute and check notebook cells.

## Implementation & Results

Since we are going to predict `price` which is a continuous numerical value, a regression algorithm must be implemented. There are several methods in scikit-learn to implement this algorithm. We tried many of them and chose the most successful one.

Algorithms we tried:
- SVR & Polynomial SVR
- KNeighborsRegressor
- GradientBoostingRegressor
- RandomForestRegressor

It seems like `SVR` is the most successful one with 58% r2 score (evaluation metric for numerical values), but it is not really a good result. We can improve this score by tuning hyper parameters of this method or doing more feature engineering or trying a different implementation of the algorithm.  
