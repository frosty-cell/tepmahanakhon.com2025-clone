<!-- SvelteKit(Svelte5): /routes/menu/+page.svelte -->
<script lang="ts">
	import MenuDropdown from '$lib/components/go/MenuDropdown.svelte';

	// --- Type Definitions ---
	type MenuItem = {
		name_th: string;
		name_en: string;
		description: string;
		price: number;
		image: string;
		special?: string;
	};

	type MenuCategory = {
		value: string;
		thai: string;
		english: string;
	};

	// --- Data ---
	const allMenuItems: Record<string, MenuItem[]> = {
		starters: [
			{
				name_th: 'ทอดมันปลาทูเทพฯ',
				name_en: 'Tod Mun Pla Too',
				description: 'เนื้อปลาทูสดตำในครกหินกับพริกแกงเผ็ดใต้ทอดกรอบๆบนใบโหระพา | Thai Mackerel crispy cake',
				price: 260,
				image: '/images/menu/1/STARTERS - Tod Mun Pla Too.png',
				special: undefined
			},
			{
				name_th: 'พล่าปลาทูใบชะพลู',
				name_en: 'Pla Pla Tu',
				description: 'ปลาทูย่างหอมพล่ากับสมุนไพรรสจัด | Thai Mackerel spicy salad',
				price: 210,
				image: '/images/menu/1/STARTERS - Pla Pla Tu.png',
				special: undefined
			},
			{
				name_th: 'กุ้งแช่น้ำปลาหอม',
				name_en: 'Kung Chae Nam Pla',
				description: 'กุ้งสดพอดีคำโตหมักน้ำปลาหอมรสดีกับซอสพริกขี้หนูสวน | shrimp with spicy fish sauce',
				price: 210,
				image: '/images/menu/1/STARTERS - Kung Chae Nam Pla.png',
				special: undefined
			},
			{
				name_th: 'ข้อไก่กระบอก',
				name_en: 'Koh Gai Krabok',
				description: 'ข้อไก่ทอดหมักเครื่องเทศรสทางใต้ | deep fried chicken cartilage soaked in spicy sauce',
				price: 230,
				image: '/images/menu/1/STARTERS - Koh Gai Krabok.png',
				special: undefined
			},
			{
				name_th: 'ข้าวแคบลับแล',
				name_en: 'Kao Kap Lub Lae',
				description: 'แผ่นแป้งทำจากข้าวเหนียว ของทานเล่นจากลับแล เมืองอุตรดิตถ์ | 5 Mystery chips',
				price: 150, // Price assumed
				image: '/images/menu/1/STARTERS - Kao Kap Lub Lae.png',
				special: undefined
			},
			{
				name_th: 'ข้าวเกรียบว่าวน้ำพริกเผา',
				name_en: 'Kao Kreab Wow',
				description: 'ข้าวโป่ง ของทานเล่นโบราณทำจากข้าวเหนียว | Thai giant rice cracker served with sweet-spicy paste',
				price: 150, // Price assumed
				image: '/images/menu/1/STARTERS - Kao Kreab Wow.png',
				special: undefined
			},
			{
				name_th: 'ถั่วสมุนไพร',
				name_en: 'Tua Samoon Prai',
				description: 'เม็ดมะม่วงหิมพานต์ ถั่วปากอ้า ถั่วลิสงคั่ว เครื่องต้มยำ | mixed nuts roasted with Thai Tom Yum herbs',
				price: 120, // Price assumed
				image: '/images/menu/1/STARTERS - Tua Samoon Prai.png',
				special: undefined
			},
			{
				name_th: 'หนอนไหม',
				name_en: 'Silkworms',
				description: 'หนอนไหมทอดสมุนไพรกรอบ | deep fried silkworms with herbs',
				price: 180, // Price assumed
				image: '/images/menu/1/STARTERS - Silkworms.png',
				special: undefined
			},
			{
				name_th: 'หมูสร่ง',
				name_en: 'Moo-Srong',
				description: 'หมูก้อนหมักพันด้วยเส้นหมี่เหลืองทอดกรอบ | deep fried pork dumpling wrapped with egg-noodles, served with plum sauce',
				price: 220, // Price assumed
				image: '/images/menu/1/STARTERS - Moo-Srong.png',
				special: undefined
			},
			{
				name_th: 'กุ้งสไบ',
				name_en: 'Goong Sabai',
				description: 'กุ้งหมักห่มด้วยเส้นหมี่เหลืองทอดกรอบ | deep fried shrimp wrapped with egg-noodles served with plum sauce',
				price: 240, // Price assumed
				image: '/images/menu/1/STARTERS - Goong Sabai.png',
				special: undefined
			},
			{
				name_th: 'เนื้อแดดเดียวสมุนไพรกรอบ',
				name_en: 'Nua Dad Diew',
				description: 'เนื้อแดดเดียวคั่วสมุนไพรกรอบ | sun-dry beef, stir-fry with chilli and topped with crispy Thai basil',
				price: 280, // Price assumed
				image: '/images/menu/1/STARTERS - Nua Dad Diew.png',
				special: undefined
			},
			{
				name_th: 'พล่าเนื้อตะใคร้หอม',
				name_en: 'Pla Nua Ta Crai Hom',
				description: 'พล่าเนื้อย่างรสจัด | spicy beef salad with lemongrass and mint',
				price: 290, // Price assumed
				image: '/images/menu/1/STARTERS - Pla Nua Ta Crai Hom.png',
				special: undefined
			},
			{
				name_th: 'พิคานย่าหมักลาบ',
				name_en: 'Crying Tiger',
				description: 'Grilled (picanha - 170g.) beef E-sarn style with jaew sauce | Farmer certified 100% Angus Grain fed 120 days',
				price: 450,
				image: '/images/menu/1/STARTERS - Crying Tiger.png',
				special: 'Mild'
			},
			{
				name_th: 'ดาหลาม้าฮ่อ',
				name_en: 'Darha Ma hor',
				description: 'pineapple slide serve with nutty, Darha flower and mushroom',
				price: 210,
				image: '/images/menu/1/STARTERS - Darha Ma hor.png',
				special: 'Vegetarian'
			},
			{
				name_th: 'ยำดอกดาหลา',
				name_en: 'Yum Dok Darha',
				description: 'refreshing spicy Darha flower salad',
				price: 210,
				image: '/images/menu/1/STARTERS - Yum Dok Darha.png',
				special: 'Vegetarian, Mild'
			},
			{
				name_th: 'ลาบทอด',
				name_en: 'Larb Tod',
				description: 'deep fried spicy plant base ball [E-sarn flaver]',
				price: 210,
				image: '/images/menu/1/STARTERS - Larb Tod.png',
				special: 'Vegetarian, Hot'
			},
			{
				name_th: 'ตำสายบัว กุ้งสด/กุ้งสุก',
				name_en: 'Som Tum Sai Bua',
				description: 'ตำสายบัวไทยใส่กุ้ง หรือ ตำสายบัวกุ้งสดใส่ปลาร้า | stem of lotus flower made into spicy Thai salad',
				price: 210,
				image: '/images/menu/1/STARTERS - Som Tum Sai Bua.png',
				special: 'Hot'
			}
		],
		grilled: [
			{
				name_th: 'เก้าย่าง',
				name_en: 'Kao Yang (grilled platter - 9 sticks)',
				description: 'รวมของย่าง 9 ไม้',
				price: 450, // Price assumed
				image: '/images/menu/2/GRILLED - Kao Yang grilled platter - 9 sticks.png',
				special: undefined
			},
			{
				name_th: 'ไก่ย่างขมิ้น',
				name_en: 'Kai Yang Kamin',
				description: 'cumin marinated grilled chicken served with tamarind sauce',
				price: 250, // Price assumed
				image: '/images/menu/2/GRILLED - Kai Yang Kamin.png',
				special: undefined
			},
			{
				name_th: 'กุ้งย่างตะไคร้',
				name_en: 'Goong Yang',
				description: 'grilled lemongrass shrimp with - 3 sticks',
				price: 280, // Price assumed
				image: '/images/menu/2/GRILLED - Goong Yang.png',
				special: undefined
			},
			{
				name_th: 'ตับไก่ย่าง',
				name_en: 'Tub Kai Yang',
				description: 'grilled chicken liver served with tamarind sauce',
				price: 180, // Price assumed
				image: '/images/menu/2/GRILLED - Tub Kai Yang.png',
				special: undefined
			},
			{
				name_th: 'ไส้กรอกขวัญ',
				name_en: 'Sai Krok Kwan',
				description: 'grilled Thai sour E-sarn sausage',
				price: 220, // Price assumed
				image: '/images/menu/2/GRILLED - Sai Krok Kwan.png',
				special: undefined
			},
			{
				name_th: 'เนื้อย่างเตาถ่าน',
				name_en: 'Charcoal Grill',
				description: 'เนื้อส่วนพิคานย่า',
				price: 450, // Price assumed
				image: '/images/menu/2/GRILLED - Charcoal Grill.png',
				special: undefined
			}
		],
		'main-dish': [
			{
				name_th: 'ผัดไทยเทพฯกุ้งกระบอก',
				name_en: 'Pad Thai Tep',
				description: 'Sukhothai recipe Pad Thai with shrimp, *contain nuts',
				price: 230,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Pad Thai Tep.png',
				special: undefined
			},
			{
				name_th: 'ข้าวเนื้อแดดเดียวกะเพรากรอบ',
				name_en: 'Khao Nua Dad Diew',
				description: 'spicy fried rice with sun-dry beef, topped with crispy Thai basil',
				price: 260,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Khao Nua Dad Diew.png',
				special: 'Mild'
			},
			{
				name_th: 'ข้าวคั่วไส้กรอกขวัญ',
				name_en: 'Khao Kua Sai Krok Kwan',
				description: 'fried rice with sour E-sarn sausage',
				price: 210,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Khao Kua Sai Krok Kwan.png',
				special: undefined
			},
			{
				name_th: 'ข้าวคั่วตับทอดกระเทียม',
				name_en: 'Khao Kua Tub Tod Kra Tiam',
				description: 'fried rice with chicken liver and crispy garlic',
				price: 210,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Khao Kua Tub Tod Kra Tiam.png',
				special: undefined
			},
			{
				name_th: 'ข้าวคั่วปลาทูสมุนไพร',
				name_en: 'Khao Kua Pla Tu',
				description: 'fried rice with Thai Mackerel and herbs',
				price: 210,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Khao Kua Pla Tu.png',
				special: undefined
			},
			{
				name_th: 'ผัดไทเทพฯ เต้าหู้ กระบอก',
				name_en: 'Pad Tai Tofu',
				description: 'Sukhothai recipe Pad Thai with tofu, *contain nuts',
				price: 230,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Pad Tai Tofu.png',
				special: 'Vegetarian'
			}
		],
		'plant-base': [
			{
				name_th: 'ดาหลาม้าฮ่อ',
				name_en: 'Darha Ma hor',
				description: 'pineapple slide serve with nutty, Darha flower and mushroom',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Darha Ma hor.png',
				special: 'Vegetarian'
			},
			{
				name_th: 'ยำดอกดาหลา',
				name_en: 'Yum Dok Darha',
				description: 'refreshing spicy Darha flower salad',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Yum Dok Darha.png',
				special: 'Vegetarian, Mild'
			},
			{
				name_th: 'ลาบทอด',
				name_en: 'Larb Tod',
				description: 'deep fried spicy plant base ball [E-sarn flaver]',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Larb Tod.png',
				special: 'Vegetarian, Hot'
			},
			{
				name_th: 'ผัดไทเทพฯ เต้าหู้ กระบอก',
				name_en: 'Pad Tai Tofu',
				description: 'Sukhothai recipe Pad Thai with tofu, *contain nuts',
				price: 230,
				image: '/images/menu/4/PLANT_BASE - Pad Tai Tofu.png',
				special: 'Vegetarian'
			},
			{
				name_th: 'ข้าวคั่วกระเพราหมูกรอบกระบอก',
				name_en: 'Khao Kua Kra Prao Mu Krob',
				description: 'spicy basil fried rice with crispy plant base',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Khao Kua Kra Prao Mu Krob.png',
				special: 'Vegetarian, Mild'
			},
			{
				name_th: 'ยำแหนมหมูกรอบทิพย์',
				name_en: 'Yum Nham Moo Krob',
				description: 'spicy sour fermented crispy plant base salad with fresh ginger, chilli, black sesame',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Yum Nham Moo Krob.png',
				special: 'Vegetarian, Mild'
			},
			{
				name_th: 'ลาบหมูกรอบทิพย์',
				name_en: 'Larb Moo Krob',
				description: 'deep fried spicy crispy plant base, seasoned with E-sarn flaver',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Larb Moo Krob.png',
				special: 'Vegetarian, Mild'
			}
		],
		'signature-drinks': [
			{
				name_th: 'สุราสมุนไพรเซท',
				name_en: 'Thai Herbal Liquor',
				description: 'รวม 3 ตัว เสิร์ฟครบชุด (พระอภัยมณี / ราชสีห์คำราม / กากี) | a taster set of 3 kinds',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - Thai Herbal Liquor.png',
				special: 'Type 1'
			},
			{
				name_th: 'สงกรานต์',
				name_en: 'SongKran',
				description: 'เปรี้ยว หวาน ดื่มง่าย ชวนให้สดชื่น | passionfruit, lime, syrup, mint',
				price: 330,
				image: '/images/menu/5/SIGNATURE_DRINKS - SongKran.png',
				special: 'Vegetarian, Type 1'
			},
			{
				name_th: 'บั้งไฟพญานาค',
				name_en: 'E-Sarn Rocket',
				description: 'สุราสมุนไพรทิ้งดิ่งลงในกระบอกไม้ไผ่ที่เต็มไปด้วยเบียร์ไทย | beer bomb with herbal liquor shot',
				price: 330,
				image: '/images/menu/5/SIGNATURE_DRINKS - E-Sarn Rocket.png',
				special: 'Type 1'
			},
			{
				name_th: 'ลอยกระทง',
				name_en: 'LOY KRA TONG',
				description: 'ลอยละล่อง แรง แต่ดื่มลื่น | Campari, syrup, egg white, flower pollen-infused liquor, dry vermouth, lime',
				price: 500,
				image: '/images/menu/5/SIGNATURE_DRINKS - LOY KRA TONG.png',
				special: 'Type 1'
			},
			{
				name_th: 'สยามสามช่า',
				name_en: 'SIAM SAMCHA [MICHELIN GALA DINNER 2023]',
				description: 'รางวัลรองชนะเลิศ Mekhong The Spirit Competition 2022 และเสริฟในงาน MICHELIN GALA DINNER 2023 | Mekhong, fire Samkler brown sugar, Samkler cordial, Aperol, sparkling rose',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - SIAM SAMCHA [MICHELIN GALA DINNER 2023].png',
				special: 'Type 2'
			},
			{
				name_th: 'แม่โขงเฉลิมไทย',
				name_en: 'Mekhong Chalerm Thai [MICHELIN GALA DINNER 2022]',
				description: 'แม่โขงเฉลิมไทย ถูกรับเชิญให้เสริฟในงาน MICHELIN GALA DINNER 2022 | Mekhong, Indian gooseberry, clove, kaffir leaves, fever tree tonic',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - Mekhong Chalerm Thai [MICHELIN GALA DINNER 2022].png',
				special: 'Type 2'
			},
			{
				name_th: 'ทอง',
				name_en: 'THONG [ MICHELIN GALA DINNER 2018 ]',
				description: 'ถูกคัดเลือกให้เสริฟในงาน Gala Michelin 2018 หอมหวานด้วยรสมะม่วงนำ้ดอกไม้ และน้ำผึ้งป่า | fresh mango, wild honey, dill, lime, syrup, egg white, pure gold leaf',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - THONG [ MICHELIN GALA DINNER 2018 ].png',
				special: 'Type 2'
			},
			{
				name_th: 'สว่างฟ้า',
				name_en: 'SA WANG FAH',
				description: 'จิน ดองเก็กฮวยป่า ชาหอมหมื่นลี้ บ๊วย และผสมด้วยโทนิคชั้นดี | local gin infused with; plum, herbs, chrysanthemum tea, Fever Tree tonic',
				price: 420,
				image: '/images/menu/5/SIGNATURE_DRINKS - SA WANG FAH.png',
				special: 'Type 2'
			},
			{
				name_th: 'เดินอากาศ',
				name_en: 'DERN AR-KAD',
				description: '2 รส ว็อดก้า รัม พริก-เกลือหิมาลายัน และสับปะรดรัม | rum, vodka, sweet & sour rimmed-glass, syrup, lime and pineapple',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - DERN AR-KAD.png',
				special: 'Type 2'
			},
			{
				name_th: 'ยามเย็น',
				name_en: 'YAM YEN',
				description: 'สดชื่น เด่นด้วยกลิ่นนำ้มันหอมระเหยจากใบโหระพา | crushed basil leaves, lime, syrup, Angostura bitter',
				price: 300,
				image: '/images/menu/5/SIGNATURE_DRINKS - YAM YEN.png',
				special: 'Type 2'
			},
			{
				name_th: 'ซ่อนอารมณ์',
				name_en: 'HIDDEN AGENDA',
				description: 'หวานซ่อนเปรี้ยว ใช้ผลไม้ตามฤดูกาล | sweet & sour taste of seasonal fruits of Thailand',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - HIDDEN AGENDA.png',
				special: 'Type 2'
			},
			{
				name_th: 'ชมดง',
				name_en: 'CHOM DONG',
				description: 'ชงแบบนิโกรนี่ ขิงตัดกับรสหวานจากอินทผาลัม และน้ำยาอุทัยทิพย์ | Negroni style cocktail with ginger, dates fruit, Campari, sweet vermouth, Thai bitter',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - CHOM DONG.png',
				special: 'Type 2'
			},
			{
				name_th: 'กาลครั้งหนึ่ง',
				name_en: 'KAL LA KRANG 1',
				description: 'จินล้ำลึก ชวนหวนคิดถึงอดีต หวานปนขม | dry gin, lime, butterfly pea and lime candy',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - KAL LA KRANG 1.png',
				special: 'Type 2'
			},
			{
				name_th: 'เอิบอันดามัน',
				name_en: 'ERB ANDAMAN',
				description: 'พาลงใต้ชมดงดอกดาหลา สาวงามที่โอบล้อมทะเลอันดามัน | Saneha craft gin, Darha cordiel, lime, Fever Tree tonic',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - ERB ANDAMAN.png',
				special: 'Type 2'
			},
			{
				name_th: 'HIGHBALL - เตยหอม',
				name_en: 'PANDAN',
				description: '(rum + pandan infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - HIGHBALL_PANDAN.png',
				special: 'Type 3 - (local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'HIGHBALL - สับปะรด',
				name_en: 'PINEAPPLE',
				description: '(rum + soda + pineapple infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - HIGHBALL_PINEAPPLE.png',
				special: 'Type 3 - (local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'HIGHBALL - บ๊วย',
				name_en: 'Plum',
				description: '(rum + plum infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - HIGHBALL_Plum.png',
				special: 'Type 3 - (local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'ชาไทย',
				name_en: 'THAI TEA',
				description: '(rum + soda + Thai tea infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - THAI TEA.png',
				special: 'Type 3 - (local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'อุทัยทิพย์',
				name_en: 'UTAITIP',
				description: '(rum + soda + Thai herbal bitter infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - UTAITIP.png',
				special: 'Type 3 - (local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'สุราชุมชน',
				name_en: 'Local Distilled Spirits',
				description: 'สุรากลั่นชุมชนรสชาติดีทั่วไทย สอบถามได้จากพนักงาน (ซอต/แก้ว) | A curated selection of premium Thai craft spirits',
				price: 350,
				image: '/images/menu/product-placeholder.png',
				special: 'Type 4'
			},
			{
				name_th: 'อุ มิกซ์เบียร์/ซอฟดริงค์',
				name_en: 'Au Mixed',
				description: 'เลือกเสิร์ฟกับ เบียร์ หรือซอฟดริ้ง | local rice wine from E-Sarn, served with beer or soft drinks',
				price: 290,
				image: '/images/menu/5/SIGNATURE_DRINKS - Au Mixed.png',
				special: 'Type 4'
			},
			{
				name_th: 'สาโทเมืองแพร่',
				name_en: 'Sato Phrae',
				description: 'สาโทจากข้าว 5 สายพันธุ์ อาทิ ข้าวเหนียวแม่โจ้ กข6 | Local rice wine made from 5 types of sticky rice [Phrae: North of TH] Alc.9.1%',
				price: 290,
				image: '/images/menu/5/SIGNATURE_DRINKS - Sato Phrae.png',
				special: 'Type 4'
			},
			{
				name_th: 'สาโทเทพนม',
				name_en: 'DEVANOM CRAFT SATO',
				description: 'คราฟท์สาโทพรีเมี่ยมรสนุ่มนวลทำจากข้าวเหนียวเขี้ยวงูเชียงราย | Premium sato crafted with care using the finest Khiew Ngu sticky rice from Chiangrai. aromatic, fruity note, ALC.6%',
				price: 290,
				image: '/images/menu/5/SIGNATURE_DRINKS - DEVANOM CRAFT SATO.png',
				special: 'Type 4'
			},
			{
				name_th: 'รวงข้าว สยามแซฟไฟร์',
				name_en: 'RUANG KHAO SIAM SAPPHIRE',
				description: 'Aged in oak casks, imparting a rich, full-bodied, and aromatic flavor. On the rock or neat',
				price: 450,
				image: '/images/menu/5/SIGNATURE_DRINKS - RUANG KHAO SIAM SAPPHIRE.png',
				special: 'Type 4'
			},
			{
				name_th: 'สุราขาวสักทองแพร่',
				name_en: 'Lao Khao',
				description: 'สุราขาวบ่มพิเศษ 35 ดีกรี ดื่มเป็นช็อตหรือสูตรผสมกระทิงแดง | Thai white spirit, strong sensation. Alc. 35%',
				price: 350,
				image: '/images/menu/5/SIGNATURE_DRINKS - Lao Khao.png',
				special: 'Type 4'
			},
			{
				name_th: 'แสงโสม + มิกซ์เซอร์',
				name_en: 'LOCAL RUM + MIXER',
				description: '',
				price: 350,
				image: '/images/menu/product-placeholder.png',
				special: 'Type 5'
			},
			{
				name_th: 'จิน โทนิค',
				name_en: 'GIN + TONIC',
				description: 'ราคา 400 - 1,000 บาท',
				price: 400,
				image: '/images/menu/product-placeholder.png',
				special: 'Type 5'
			},
			{
				name_th: 'จินไทย โทนิค',
				name_en: 'THAI GIN + TONIC',
				description: 'We use Fever Tree Tonic, and Iron Balls Gin',
				price: 450,
				image: '/images/menu/5/SIGNATURE_DRINKS - THAI GIN+ TONIC.png',
				special: 'Type 5'
			},
			{
				name_th: 'วิสกี้ เบอร์เบิ้น วอดก้า + มิกซ์เซอร์',
				name_en: 'SCOTH WHISKY / VODKA / BOURBON / + MIXER',
				description: 'ราคา 400-1,000 บาท',
				price: 400,
				image: '/images/menu/product-placeholder.png',
				special: 'Type 5'
			},
			{
				name_th: 'วิสกี้แบบซิงเกิ้ลมอลท์',
				name_en: 'SINGLE MALT WHISKY',
				description: 'เสิร์ฟกับน้ำแข็งมวลแน่น ใสบริสุทธิ์ | by shot, on the rock or neat, we use high quality rock ice',
				price: 400,
				image: '/images/menu/product-placeholder.png',
				special: 'Type 5'
			},
			{
				name_th: 'น้ําแร่',
				name_en: 'MINERAL WATER',
				description: '(Sai Yok Springs still water - 250 ml.)',
				price: 50,
				image: '/images/menu/5/SIGNATURE_DRINKS - MINERAL WATER.png',
				special: 'Type 6'
			},
			{
				name_th: 'น้ําแร่มีฟอง',
				name_en: 'SPARKLING WATER',
				description: 'Sai Yok Springs sparkling water - 250 ml',
				price: 120,
				image: '/images/menu/5/SIGNATURE_DRINKS - SPARKLING WATER.png',
				special: 'Type 6'
			},
			{
				name_th: 'น้ำเกสรดอกมะพร้าว',
				name_en: 'COCONUT PILLEN FLOWER',
				description: 'ของดีจากแม่กลอง ความหวานจากธรรมชาติ สดชื่น สุดฟิน | Non-alcoholic',
				price: 210,
				image: '/images/menu/5/SIGNATURE_DRINKS - COCONUT PILLEN FLOWER.png',
				special: 'Vegetarian, Type 6'
			},
			{
				name_th: 'เปิดบริสุทธ์',
				name_en: 'Like A Virgin',
				description: 'ตะไคร้ ใบเตย | lemongrass and pandan syrup, lime',
				price: 230,
				image: '/images/menu/5/SIGNATURE_DRINKS - Like A Virgin.png',
				special: 'Vegetarian, Type 6'
			},
			{
				name_th: 'โทนิคฟีเวอร์ทรี',
				name_en: 'Fever Tree Tonic',
				description: '',
				price: 150,
				image: '/images/menu/5/SIGNATURE_DRINKS - Fever Tree Tonic.png',
				special: 'Type 6'
			},
			{
				name_th: 'โซดา น้ำอัดลม',
				name_en: 'Soft drinks',
				description: 'โค้ก / สไปรท์ / โซดา | Coke / Sprite / Soda',
				price: 100,
				image: '/images/menu/5/SIGNATURE_DRINKS - Soft drinks.png',
				special: 'Type 6'
			}
		],
		'beer-wine': [
			{
				name_th: 'MAKMAO WINE (Red)',
				name_en: 'MAKMAO WINE (Red)',
				description: 'ไวน์แดง ไทย (สกลนคร), Mak Mao berry; เบอร์รี่และผลไม้สด | Red wine, Thailand (Sakon Nakhon); organic Mak Mao berry – fresh fruit notes & berry',
				price: 1400,
				image: '/images/menu/6/BEER_WINE - MAKMAO WINE (Red).png',
				special: undefined
			},
			{
				name_th: 'THONGKHAM ESTATE (Red)',
				name_en: 'THONGKham ESTATE (Red)',
				description: 'ไวน์แดงไทย (เชียงราย)ทองคำ เอสเตท ปิโนต์ นัวร์ 2022 — เชอร์รี่ ราสเบอร์รี่ วานิลลา โอ๊ค | Red Wine Thailand (Chiang Rai) Thongkham Estate Pinot Noir 2022',
				price: 1500,
				image: '/images/menu/6/BEER_WINE - THONGKHAM ESTATE (Red).png',
				special: undefined
			},
			{
				name_th: 'GRANMONTE SAKUNA (Rosé)',
				name_en: 'GRANMONTE SAKUNA (Rosé)',
				description: 'ไวน์โรเซ่ไทย (เขาใหญ่)กรามอนเต้ สกุณา โรเซ่ — สีชมพูใสเบอร์รี่ รสนุ่ม หวานบาง สดชื่น | Rosé Wine Thailand (Khao Yai) GranMonte Sakuna Rosé',
				price: 1500,
				image: '/images/menu/6/BEER_WINE - GRANMONTE SAKUNA (Rosé).png',
				special: undefined
			},
			{
				name_th: 'LAMADOR (Red)',
				name_en: 'LAMADOR (Red)',
				description: 'ไวน์แดง ชิลี, Merlot 2019; ผลไม้แดง & ดอกไวโอเล็ต | Red wine, Chile; Merlot 2019 – red fruit & violet floral notes',
				price: 1500,
				image: '/images/menu/6/BEER_WINE - LAMADOR (Red).png',
				special: undefined
			},
			{
				name_th: 'FINIMONDO (Red)',
				name_en: 'FINIMONDO (Red)',
				description: 'ไวน์แดง อิตาลี, Nero d’Avola & Syrah; เบอร์รี่ ยาสูบ เครื่องเทศ | Red wine, Italy; Nero d’Avola & Syrah – intense berry, tobacco & spice',
				price: 2000,
				image: '/images/menu/6/BEER_WINE - FINIMONDO (Red).png',
				special: undefined
			},
			{
				name_th: 'GRANMONTE VIOGNIER (White)',
				name_en: 'GRANMONTE VIOGNIER (White)',
				description: 'ไวน์ขาวไทย (เขาใหญ่)กรามอนเต้ วิอองเย่ 2024 — ดอกไม้เมืองร้อน แร่ธาตุ โอ๊ค | White Wine Thailand (Khao Yai) GranMonte Viognier 2024',
				price: 1500,
				image: '/images/menu/6/BEER_WINE - GRANMONTE VIOGNIER (White).png',
				special: undefined
			},
			{
				name_th: 'PÃ ROAD (White)',
				name_en: 'PÃ ROAD (White)',
				description: 'ไวน์ขาว นิวซีแลนด์ (Marlborough), Sauvignon Blanc 2023; ดอกไม้ ซิตรัส และเครื่องเทศ | White wine, New Zealand (Marlborough); Sauvignon Blanc 2023',
				price: 1800,
				image: '/images/menu/6/BEER_WINE - PÃ ROAD (White).png',
				special: undefined
			},
			{
				name_th: '7 CASINE (Sparkling)',
				name_en: '7 CASINE (Sparkling)',
				description: 'ไวน์ขาว อิตาลี, Prosecco DOC; เบา ดราย ฟองนุ่ม | White wine, Italy; Prosecco DOC – light, dry & fine bubbles',
				price: 1600,
				image: '/images/menu/6/BEER_WINE - 7 CASINE (Sparkling).png',
				special: undefined
			},
			{
				name_th: 'ชาละวัน',
				name_en: 'CHALAWAN BEER',
				description: '(PALE ALE) 4.7% ALC. (small bottle)',
				price: 280,
				image: '/images/menu/6/BEER_WINE - CHALAWAN BEER.png',
				special: undefined
			},
			{
				name_th: 'บุษบา',
				name_en: 'BUSSABA BEER',
				description: 'wheat Beer จากภูเก็ต',
				price: 280,
				image: '/images/menu/6/BEER_WINE - BUSSABA BEER.png',
				special: undefined
			},
			{
				name_th: 'สิงห์',
				name_en: 'SINGHA BEER',
				description: '(LAGER BEER) 5% ALC. (small bottle)',
				price: 250,
				image: '/images/menu/6/BEER_WINE - SINGHA BEER.png',
				special: undefined
			}
		],
		dessert: [
			{
				name_th: 'จินดามณี',
				name_en: 'CHINDA MANEE',
				description: 'ข้าวเหนียวมูน 3 หน้า มะม่วงน้ำดอกไม้ + กระฉีก มะพร้าวทึนทึก + ทองหยอดหยาดเพชร สูตรไข่เค็ม | Mango sticky rice with shredded coconut and baby Thong yod (eggdrop sweet)',
				price: 180,
				image: '/images/menu/7/DESSERT - CHINDA MANEE.png',
				special: undefined
			}
		]
	};

	const menuCategories: MenuCategory[] = [
		{ value: 'starters', thai: 'ทานเล่น', english: 'STARTERS' },
		{ value: 'grilled', thai: 'เตาถ่าน', english: 'GRILLED' },
		{ value: 'main-dish', thai: 'อิ่มในกระบอก', english: 'MAIN DISHES' },
		{ value: 'plant-base', thai: 'อาหารจากพืช', english: 'PLANT BASE' },
		{ value: 'signature-drinks', thai: 'เครื่องดื่มเทพฯ', english: 'SIGNATURE DRINKS' },
		{ value: 'beer-wine', thai: 'BEER & WINE', english: '' },
		{ value: 'dessert', thai: 'ของหวานเทพฯ', english: 'DESSERT' }
	];

	// --- State ---
	let selectedCategoryValue = $state('starters');

	// --- Derived State ---
	let displayedItems = $derived(allMenuItems[selectedCategoryValue] ?? []);
</script>

<svelte:head>
    <title>[Clone] Menu | TEP BAR</title>
</svelte:head>

<main style="place-self: center; padding: 1rem 0 1rem;">
    <section>
        <h2 style="text-align: center;">Welcome to Tep Bar — Thailand’s Cultural Bar.</h2>
        <div class="context-box">
            <p>Business hours: 18:00–00:00 <br> Live music: 20:00–23:15 daily</p>
        </div>
        <div class="context-box">
            <p>Thank you for supporting our live music with a minimum spend of 500 THB/person. <br>
                💳 Payment by credit/debit card, PromptPay, Alipay, or bank transfer only. <br>
                Cash not accepted — tips in cash are welcome.
            </p>
        </div>
        <div class="context-box">
            <p>ขอบพระคุณลูกค้าทุกท่านสำหรับการใช้จ่ายขั้นต่ำ 500 บาทต่อท่าน<br>
                💳 ทางร้านรับชำระผ่านบัตรเครดิต/เดบิต,<br>
                พร้อมเพย์, Alipay<br>
                หรือโอนผ่านบัญชีธนาคารเท่านั้น<br>
                ไม่รับเงินสด แต่สามารถให้ทิปทีมงานเป็นเงินสดได้<br>
                _________<br>
            </p>
        </div>
    </section>
        <div class="spacer"></div>  
    <section class="select-section">
        <MenuDropdown items={menuCategories} bind:selectedValue={selectedCategoryValue} />
    </section>

    <div style="text-align: center; margin-top: 1rem; color: #666;">
        Selected Value: {selectedCategoryValue}
    </div>

    <!-- <div class="menu-container">
        <div class="menu-card">
            <img src="/images/menu/1/STARTERS - Tod Mun Pla Too.png" alt="ทอดมันปลาทูเทพฯ">
            <div>
                <h5>★ ทอดมันปลาทูเทพฯ | Tod Mun Pla Too</h5>
                <p>เนื้อปลาทูสดตำในครกหินกับพริกแกงเผ็ดใต้ทอดกรอบๆบนใบโหระพา | Thai Mackerel crispy cake</p>
            </div>
            <p>฿260</p>
        </div>
        <div class="menu-card">
            <img src="/images/menu/1/STARTERS - Pla Pla Tu.png" alt="พล่าปลาทูใบชะพลู">
            <div>
                <h5>★ พล่าปลาทูใบชะพลู | Pla Pla Tu</h5>
                <p>ปลาทูย่างหอมพล่ากับสมุนไพรรสจัด | Thai Mackerel spicy salad</p>
            </div>
            <p>฿210</p>
        </div>
        <div class="menu-card">
            <img src="/images/menu/1/STARTERS - Kung Chae Nam Pla.png" alt="กุ้งแช่น้ำปลาหอม">
            <div>
                <h5>★ กุ้งแช่น้ำปลาหอม | Kung Chae Nam Pla</h5>
                <p>กุ้งสดพอดีคำโตหมักน้ำปลาหอมรสดีกับซอสพริกขี้หนูสวน | shrimp with spicy fish sauce</p>
            </div>
            <p>฿210</p>
        </div>

        <div class="menu-card">
            <img src="/images/menu/1/STARTERS - Koh Gai Krabok.png" alt="กุ้งแช่น้ำปลาหอม">
            <div>
                <h5>★ ข้อไก่กระบอก | Koh Gai Krabok</h5>
                <p>ข้อไก่ทอดหมักเครื่องเทศรสทางใต้ | deep fried chicken cartilage soaked in spicy sauce</p>
            </div>
            <p>฿230</p>
        </div>
    </div> -->

    <div class="menu-container">
		{#each displayedItems as item}
			<div class="menu-card">
                <div>
                    <img src={item.image} alt={item.name_th} />
                    <h5 style="font-size: 18px;">★ {item.name_th} | {item.name_en}</h5>
                </div>
				<div>
					<p style="font-size: 15px;">{item.description}</p>
				</div>
				<p style="font-size: 18px;">฿{item.price}</p>
			</div>
		{/each}
	</div>
    
</main>

<style>
    .spacer {
        height: 50px;
    }

    .context-box {
        padding: 1rem; text-align: center;
    }

    .select-section {
        display: flex;
        justify-content: center; /* จัดให้อยู่กลางแนวนอน */
    }

    /* menu card */
    .menu-container {
        display: grid;
        grid-template-columns: repeat(3, 1fr); /* 3 คอลัมน์ กว้างเท่ากัน */
        padding: 0.5rem;
        width: 750px;
        font-weight: 200;
    }
    .menu-card {
        /* border: 1px solid #eee; */
        /* box-shadow: 0 2px 4px rgba(0,0,0,0.05); */
        
        border-radius: 8px;
        padding: 0.51rem;
        text-align: center;
        line-height: 2rem;
        display: flex;
        flex-direction: column;
        justify-content: sta;
        gap: 10px;
    }

    .menu-card img {
        width: 100%;
        aspect-ratio: 1 / 1; /* ทำให้รูปเป็นสี่เหลี่ยมจัตุรัส */
        object-fit: cover;
        border-radius: 4px;
    }
    /* menu card */
</style>