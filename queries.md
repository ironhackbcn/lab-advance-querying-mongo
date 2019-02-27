![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# Answers

### 1. All the companies that it's name match 'Babelgum'. Retrieve only their `name` field.

> db.companies.find(     {name: "Babelgum"},     {name: 1, _id:0} );

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.

> db.companies.find({number_of_employees:{$gt:5000}}).sort({number_of_employees: 1}).limit(20)

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fileds.

db.companies.find(
    {
        founded_year:{
            $gte: 2000,
            $lte: 2500
        }
    },
    {
        name: 1,
        founded_year: 1,
        _id: 0
    }
)

### 4. All the companies that had a Valuation Amount of more than 100.000.000 and have been founded before 2010. Retrieve only the `name` and `ipo` fields.

> db.companies.find({$and:[{"ipo.valuation_amount":{$gt:100000000}},{founded_year:{$lt:2010}}]},{name:1, ipo:1, _id:0})

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.

db.companies.find(
    {$and:[{number_of_employees:{$lt: 1000}},{founded_year:{$lt: 2005}}]}
).sort({number_of_employees:1}).limit(10)

### 6. All the companies that don't include the `partners` field.

db.companies.find({"partners.0": {$exists:false}}, {name:1, _id:0})

### 7. All the companies that have a null type of value on the `category_code` field.

db.companies.find({category_code: null}, {_id:0, name:1})

### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.

db.companies.find(
    {$and:[{number_of_employees:{$gte:100}}, {number_of_employees:{$lt:1000}}]},
    {name: 1, number_of_employees: 1, _id:0}
)

### 9. Order all the companies by their IPO price descendently.

db.companies.find(
    {"ipo.valuation_amount": {$exists: true, $ne: null}},
    {_id:0, name: 1, "ipo.valuation_amount":1}
).sort({"ipo.valuation_amount": -1})

### 10. Retrieve the 10 companies with more employees, order by the `number of employees`

db.companies.find({}, {_id:0, "name": 1, "number_of_employees": 1}).sort({"number_of_employees": -1}).limit(10)

### 11. All the companies founded (founded_month) on the second semester of the year. Limit your search to 1000 companies.

db.companies.find(
    {"founded_month": {$gte: 7, $lte: 12}},
    {_id: false, "name": true, "founded_month": true}
).limit(1000);

### 12. All the companies that have been 'deadpooled' after the third year.

<!-- Your Code Goes Here -->

### 13. All the companies founded before 2000 that have and acquisition amount of more than 10.000.000

<!-- Your Code Goes Here -->

### 14. All the companies that have been acquired after 2015, order by the acquisition amount, and retrieve only their `name` and `acquisiton` field.

<!-- Your Code Goes Here -->

### 15. Order the companies by their `founded year`, retrieving only their `name` and `founded year`.

<!-- Your Code Goes Here -->

### 16. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `aquisition price` descendently. Limit the search to 10 documents.

<!-- Your Code Goes Here -->

### 17. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascendant order.

<!-- Your Code Goes Here -->

### 18. All the companies which their acquisition amount is more than 10.000.000, and currency are 'EUR'.

<!-- Your Code Goes Here -->

### 19. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.

<!-- Your Code Goes Here -->

### 20. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.

<!-- Your Code Goes Here -->

> db.companies.find(     {name: "Babelgum"},     {name: 1, _id:0} );

db.companies.find(
    {
        founded_year:{
            $gte: 2000,
            $lte: 2500
        }
    },
    {
        name: 1,
        founded_year: 1,
        _id: 0
    }
)


<!-- 
{
	"_id" : ObjectId("52cdef7c4bab8bd675297d8a"),
	"name" : "Wetpaint",
	"permalink" : "abc2",
	"crunchbase_url" : "http://www.crunchbase.com/company/wetpaint",
	"homepage_url" : "http://wetpaint-inc.com",
	"blog_url" : "http://digitalquarters.net/",
	"blog_feed_url" : "http://digitalquarters.net/feed/",
	"twitter_username" : "BachelrWetpaint",
	"category_code" : "web",
	"number_of_employees" : 47,
	"founded_year" : 2005,
	"founded_month" : 10,
	"founded_day" : 17,
	"deadpooled_year" : 1,
	"tag_list" : "wiki, seattle, elowitz, media-industry, media-platform, social-distribution-system",
	"alias_list" : "",
	"email_address" : "info@wetpaint.com",
	"phone_number" : "206.859.6300",
	"description" : "Technology Platform Company",
	"created_at" : ISODate("2007-05-25T06:51:27Z"),
	"updated_at" : "Sun Dec 08 07:15:44 UTC 2013",
	"overview" : "<p>Wetpaint is a technology platform company that uses its proprietary state-of-the-art technology and expertise in social media to build and monetize audiences for digital publishers. Wetpaint’s own online property, Wetpaint Entertainment, an entertainment news site that attracts more than 12 million unique visitors monthly and has over 2 million Facebook fans, is a proof point to the company’s success in building and engaging audiences. Media companies can license Wetpaint’s platform which includes a dynamic playbook tailored to their individual needs and comprehensive training. Founded by Internet pioneer Ben Elowitz, and with offices in New York and Seattle, Wetpaint is backed by Accel Partners, the investors behind Facebook.</p>",
	"image" : {
		"available_sizes" : [
			[
				[
					150,
					75
				],
				"assets/images/resized/0000/3604/3604v14-max-150x150.jpg"
			],
			[
				[
					250,
					125
				],
				"assets/images/resized/0000/3604/3604v14-max-250x250.jpg"
			],
			[
				[
					450,
					225
				],
				"assets/images/resized/0000/3604/3604v14-max-450x450.jpg"
			]
		]
	},
	"products" : [
		{
			"name" : "Wikison Wetpaint",
			"permalink" : "wetpaint-wiki"
		},
		{
			"name" : "Wetpaint Social Distribution System",
			"permalink" : "wetpaint-social-distribution-system"
		}
	],
	"relationships" : [
		{
			"is_past" : false,
			"title" : "Co-Founder and VP, Social and Audience Development",
			"person" : {
				"first_name" : "Michael",
				"last_name" : "Howell",
				"permalink" : "michael-howell"
			}
		},
		{
			"is_past" : false,
			"title" : "Co-Founder/CEO/Board of Directors",
			"person" : {
				"first_name" : "Ben",
				"last_name" : "Elowitz",
				"permalink" : "ben-elowitz"
			}
		},
		{
			"is_past" : false,
			"title" : "COO/Board of Directors",
			"person" : {
				"first_name" : "Rob",
				"last_name" : "Grady",
				"permalink" : "rob-grady"
			}
		},
		{
			"is_past" : false,
			"title" : "SVP, Strategy and Business Development",
			"person" : {
				"first_name" : "Chris",
				"last_name" : "Kollas",
				"permalink" : "chris-kollas"
			}
		},
		{
			"is_past" : false,
			"title" : "Board",
			"person" : {
				"first_name" : "Theresia",
				"last_name" : "Ranzetta",
				"permalink" : "theresia-ranzetta"
			}
		},
		{
			"is_past" : false,
			"title" : "Board Member",
			"person" : {
				"first_name" : "Gus",
				"last_name" : "Tai",
				"permalink" : "gus-tai"
			}
		},
		{
			"is_past" : false,
			"title" : "Board",
			"person" : {
				"first_name" : "Len",
				"last_name" : "Jordan",
				"permalink" : "len-jordan"
			}
		},
		{
			"is_past" : false,
			"title" : "Head of Technology and Product",
			"person" : {
				"first_name" : "Alex",
				"last_name" : "Weinstein",
				"permalink" : "alex-weinstein"
			}
		},
		{
			"is_past" : true,
			"title" : "CFO",
			"person" : {
				"first_name" : "Bert",
				"last_name" : "Hogue",
				"permalink" : "bert-hogue"
			}
		},
		{
			"is_past" : true,
			"title" : "CFO/ CRO",
			"person" : {
				"first_name" : "Brian",
				"last_name" : "Watkins",
				"permalink" : "brian-watkins"
			}
		},
		{
			"is_past" : true,
			"title" : "Senior Vice President, Marketing",
			"person" : {
				"first_name" : "Rob",
				"last_name" : "Grady",
				"permalink" : "rob-grady"
			}
		},
		{
			"is_past" : true,
			"title" : "VP, Technology and Product",
			"person" : {
				"first_name" : "Werner",
				"last_name" : "Koepf",
				"permalink" : "werner-koepf"
			}
		},
		{
			"is_past" : true,
			"title" : "VP Marketing",
			"person" : {
				"first_name" : "Kevin",
				"last_name" : "Flaherty",
				"permalink" : "kevin-flaherty"
			}
		},
		{
			"is_past" : true,
			"title" : "VP User Experience",
			"person" : {
				"first_name" : "Alex",
				"last_name" : "Berg",
				"permalink" : "alex-berg"
			}
		},
		{
			"is_past" : true,
			"title" : "VP Engineering",
			"person" : {
				"first_name" : "Steve",
				"last_name" : "McQuade",
				"permalink" : "steve-mcquade"
			}
		},
		{
			"is_past" : true,
			"title" : "Executive Editor",
			"person" : {
				"first_name" : "Susan",
				"last_name" : "Mulcahy",
				"permalink" : "susan-mulcahy"
			}
		},
		{
			"is_past" : true,
			"title" : "VP Business Development",
			"person" : {
				"first_name" : "Chris",
				"last_name" : "Kollas",
				"permalink" : "chris-kollas"
			}
		}
	],
	"competitions" : [
		{
			"competitor" : {
				"name" : "Wikia",
				"permalink" : "wikia"
			}
		},
		{
			"competitor" : {
				"name" : "JotSpot",
				"permalink" : "jotspot"
			}
		},
		{
			"competitor" : {
				"name" : "Socialtext",
				"permalink" : "socialtext"
			}
		},
		{
			"competitor" : {
				"name" : "Ning by Glam Media",
				"permalink" : "ning"
			}
		},
		{
			"competitor" : {
				"name" : "Soceeo",
				"permalink" : "soceeo"
			}
		},
		{
			"competitor" : {
				"name" : "Yola",
				"permalink" : "yola"
			}
		},
		{
			"competitor" : {
				"name" : "SocialGO",
				"permalink" : "socialgo"
			}
		},
		{
			"competitor" : {
				"name" : "IslamNor",
				"permalink" : "islamnor"
			}
		}
	],
	"providerships" : [ ],
	"total_money_raised" : "$39.8M",
	"funding_rounds" : [
		{
			"id" : 888,
			"round_code" : "a",
			"source_url" : "http://seattlepi.nwsource.com/business/246734_wiki02.html",
			"source_description" : "",
			"raised_amount" : 5250000,
			"raised_currency_code" : "USD",
			"funded_year" : 2005,
			"funded_month" : 10,
			"funded_day" : 1,
			"investments" : [
				{
					"company" : null,
					"financial_org" : {
						"name" : "Frazier Technology Ventures",
						"permalink" : "frazier-technology-ventures"
					},
					"person" : null
				},
				{
					"company" : null,
					"financial_org" : {
						"name" : "Trinity Ventures",
						"permalink" : "trinity-ventures"
					},
					"person" : null
				}
			]
		},
		{
			"id" : 889,
			"round_code" : "b",
			"source_url" : "http://pulse2.com/2007/01/09/wiki-builder-website-wetpaint-welcomes-95m-funding/",
			"source_description" : "",
			"raised_amount" : 9500000,
			"raised_currency_code" : "USD",
			"funded_year" : 2007,
			"funded_month" : 1,
			"funded_day" : 1,
			"investments" : [
				{
					"company" : null,
					"financial_org" : {
						"name" : "Accel Partners",
						"permalink" : "accel-partners"
					},
					"person" : null
				},
				{
					"company" : null,
					"financial_org" : {
						"name" : "Frazier Technology Ventures",
						"permalink" : "frazier-technology-ventures"
					},
					"person" : null
				},
				{
					"company" : null,
					"financial_org" : {
						"name" : "Trinity Ventures",
						"permalink" : "trinity-ventures"
					},
					"person" : null
				}
			]
		},
		{
			"id" : 2312,
			"round_code" : "c",
			"source_url" : "http://www.accel.com/news/news_one_up.php?news_id=185",
			"source_description" : "Accel",
			"raised_amount" : 25000000,
			"raised_currency_code" : "USD",
			"funded_year" : 2008,
			"funded_month" : 5,
			"funded_day" : 19,
			"investments" : [
				{
					"company" : null,
					"financial_org" : {
						"name" : "DAG Ventures",
						"permalink" : "dag-ventures"
					},
					"person" : null
				},
				{
					"company" : null,
					"financial_org" : {
						"name" : "Accel Partners",
						"permalink" : "accel-partners"
					},
					"person" : null
				},
				{
					"company" : null,
					"financial_org" : {
						"name" : "Trinity Ventures",
						"permalink" : "trinity-ventures"
					},
					"person" : null
				},
				{
					"company" : null,
					"financial_org" : {
						"name" : "Frazier Technology Ventures",
						"permalink" : "frazier-technology-ventures"
					},
					"person" : null
				}
			]
		}
	],
	"investments" : [ ],
	"acquisition" : {
		"price_amount" : 30000000,
		"price_currency_code" : "USD",
		"term_code" : "cash_and_stock",
		"source_url" : "http://allthingsd.com/20131216/viggle-tries-to-bulk-up-its-social-tv-business-by-buying-wetpaint/?mod=atdtweet",
		"source_description" : " Viggle Tries to Bulk Up Its Social TV Business by Buying Wetpaint",
		"acquired_year" : 2013,
		"acquired_month" : 12,
		"acquired_day" : 16,
		"acquiring_company" : {
			"name" : "Viggle",
			"permalink" : "viggle"
		}
	},
	"acquisitions" : [ ],
	"offices" : [
		{
			"description" : "",
			"address1" : "710 - 2nd Avenue",
			"address2" : "Suite 1100",
			"zip_code" : "98104",
			"city" : "Seattle",
			"state_code" : "WA",
			"country_code" : "USA",
			"latitude" : 47.603122,
			"longitude" : -122.333253
		},
		{
			"description" : "",
			"address1" : "270 Lafayette Street",
			"address2" : "Suite 505",
			"zip_code" : "10012",
			"city" : "New York",
			"state_code" : "NY",
			"country_code" : "USA",
			"latitude" : 40.7237306,
			"longitude" : -73.9964312
		}
	],
	"milestones" : [
		{
			"id" : 5869,
			"description" : "Wetpaint named in Lead411's Hottest Seattle Companies list",
			"stoned_year" : 2010,
			"stoned_month" : 6,
			"stoned_day" : 8,
			"source_url" : "http://www.lead411.com/seattle-companies.html",
			"source_text" : null,
			"source_description" : "LEAD411 LAUNCHES \"HOTTEST SEATTLE COMPANIES\" AWARDS",
			"stoneable_type" : "Company",
			"stoned_value" : null,
			"stoned_value_type" : null,
			"stoned_acquirer" : null,
			"stoneable" : {
				"name" : "Wetpaint",
				"permalink" : "wetpaint"
			}
		},
		{
			"id" : 8702,
			"description" : "Site-Builder Wetpaint Makes One For Itself, Using the Demand Media Playbook",
			"stoned_year" : 2010,
			"stoned_month" : 9,
			"stoned_day" : 6,
			"source_url" : "http://mediamemo.allthingsd.com/20100906/site-builder-wetpaint-makes-one-for-itself-using-the-demand-media-playbook/",
			"source_text" : null,
			"source_description" : "All Things D",
			"stoneable_type" : "Company",
			"stoned_value" : null,
			"stoned_value_type" : null,
			"stoned_acquirer" : null,
			"stoneable" : {
				"name" : "Wetpaint",
				"permalink" : "wetpaint"
			}
		}
	],
	"video_embeds" : [ ],
	"screenshots" : [
		{
			"available_sizes" : [
				[
					[
						150,
						86
					],
					"assets/images/resized/0016/0929/160929v2-max-150x150.png"
				],
				[
					[
						250,
						143
					],
					"assets/images/resized/0016/0929/160929v2-max-250x250.png"
				],
				[
					[
						450,
						258
					],
					"assets/images/resized/0016/0929/160929v2-max-450x450.png"
				]
			],
			"attribution" : null
		}
	],
	"external_links" : [
		{
			"external_url" : "http://www.geekwire.com/2011/rewind-ben-elowitz-wetpaint-ceo-building-type-media-company",
			"title" : "GeekWire interview: Rewind - Ben Elowitz, Wetpaint CEO, on building a new type of media company"
		},
		{
			"external_url" : "http://techcrunch.com/2012/06/17/search-and-social-how-two-will-soon-become-one/",
			"title" : "Guest post by CEO Ben Elowitz in TechCrunch"
		},
		{
			"external_url" : "http://allthingsd.com/20120516/what-to-expect-when-facebook-is-expecting-five-predictions-for-facebooks-first-public-year/",
			"title" : "Guest post by CEO Ben Elowitz in AllThingsD"
		},
		{
			"external_url" : "http://adage.com/article/digitalnext/facebook-biggest-player-advertising-s-540-billion-world/235708/",
			"title" : "Guest post by CEO Ben Elowitz in AdAge"
		},
		{
			"external_url" : "http://www.businessinsider.com/facebook-captures-14-percent-of-our-online-attention-but-only-4-percent-of-ad-spending-online-2012-6",
			"title" : "Guest post by CEO Ben Elowitz in Business Insider"
		},
		{
			"external_url" : "http://allfacebook.com/wetpaint-media-data_b75963",
			"title" : "AllFacebook coverage of Wetpaint"
		},
		{
			"external_url" : "http://adage.com/article/digital/celeb-site-wetpaint-shows-media-profit-facebook/237828/",
			"title" : "Profile of Wetpaint in Ad Age"
		},
		{
			"external_url" : "http://allthingsd.com/20121018/how-to-boost-your-facebook-traffic-tips-and-tricks-from-wetpaint/",
			"title" : "Interview with Wetpaint CEO Ben Elowitz in All Things D"
		},
		{
			"external_url" : "http://www.xconomy.com/seattle/2012/10/19/wetpaint-starts-licensing-its-facebook-based-media-distribution-tech/",
			"title" : "Profile of Wetpaint in Xconomy"
		}
	],
	"partners" : [ ]
} -->
