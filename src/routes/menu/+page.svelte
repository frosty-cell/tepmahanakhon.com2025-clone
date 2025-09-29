<!-- SvelteKit(Svelte5): /routes/menu/+page.svelte -->
<script lang="ts">
	import MenuDropdown from '$lib/components/go/MenuDropdown.svelte';
    import Icon from '$lib/components/go/Icon.svelte';

	// --- Type Definitions ---
	type MenuItem = {
		name_th: string;
		name_en: string;
		description: string;
		price: number;
		image: string;
		special_ingredient?: string; // เปลี่ยนชื่อเพื่อความชัดเจน
		type?: string; // เพิ่ม key ใหม่สำหรับเก็บ Type โดยเฉพาะ
	};

	type MenuCategory = {
		value: string;
		thai: string;
		english: string;
        sub_head: string;
        description?: string;
	};

	// --- Data ---
	const allMenuItems: Record<string, MenuItem[]> = {
		starters: [
			{
				name_th: 'ทอดมันปลาทูเทพฯ',
				name_en: 'Tod Mun Pla Too',
				description: 'เนื้อปลาทูสดตำในครกหินกับพริกแกงเผ็ดใต้ทอดกรอบๆบนใบโหระพา | Thai Mackerel crispy cake',
				price: 260,
				image: '/images/menu/1/STARTERS - Tod Mun Pla Too.avif',
				special_ingredient: "Hot"
			},
			{
				name_th: 'พล่าปลาทูใบชะพลู',
				name_en: 'Pla Pla Tu',
				description: 'ปลาทูย่างหอมพล่ากับสมุนไพรรสจัด | Thai Mackerel spicy salad',
				price: 210,
				image: '/images/menu/1/STARTERS - Pla Pla Tu.avif',
				special_ingredient: "Hot"
			},
			{
				name_th: 'กุ้งแช่น้ำปลาหอม',
				name_en: 'Kung Chae Nam Pla',
				description: 'กุ้งสดพอดีคำโตหมักน้ำปลาหอมรสดีกับซอสพริกขี้หนูสวน | shrimp with spicy fish sauce',
				price: 210,
				image: '/images/menu/1/STARTERS - Kung Chae Nam Pla.avif',
				special_ingredient: "Mild"
			},
			{
				name_th: 'ข้อไก่กระบอก',
				name_en: 'Koh Gai Krabok',
				description: 'ข้อไก่ทอดหมักเครื่องเทศรสทางใต้ | deep fried chicken cartilage soaked in spicy sauce',
				price: 230,
				image: '/images/menu/1/STARTERS - Koh Gai Krabok.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ข้าวแคบลับแล',
				name_en: 'Kao Kap Lub Lae',
				description: 'แผ่นแป้งทำจากข้าวเหนียว ของทานเล่นจากลับแล เมืองอุตรดิตถ์ | 5 Mystery chips',
				price: 150, // Price assumed
				image: '/images/menu/1/STARTERS - Kao Kap Lub Lae.avif',
				special_ingredient: "Mild, Vegan"
			},
			{
				name_th: 'ข้าวเกรียบว่าวน้ำพริกเผา',
				name_en: 'Kao Kreab Wow',
				description: 'ข้าวโป่ง ของทานเล่นโบราณทำจากข้าวเหนียว | Thai giant rice cracker served with sweet-spicy paste',
				price: 150, // Price assumed
				image: '/images/menu/1/STARTERS - Kao Kreab Wow.avif',
				special_ingredient: "Vegetarian, Mild, Vegan,"
			},
			{
				name_th: 'ถั่วสมุนไพร',
				name_en: 'Tua Samoon Prai',
				description: 'เม็ดมะม่วงหิมพานต์ ถั่วปากอ้า ถั่วลิสงคั่ว เครื่องต้มยำ | mixed nuts roasted with Thai Tom Yum herbs',
				price: 120, // Price assumed
				image: '/images/menu/1/STARTERS - Tua Samoon Prai.avif',
				special_ingredient: 'Vegetarian, Mild, Organic, Vegan'
			},
			{
				name_th: 'หนอนไหม',
				name_en: 'Silkworms',
				description: 'หนอนไหมทอดสมุนไพรกรอบ | deep fried silkworms with herbs',
				price: 180, // Price assumed
				image: '/images/menu/1/STARTERS - Silkworms.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'หมูสร่ง',
				name_en: 'Moo-Srong',
				description: 'หมูก้อนหมักพันด้วยเส้นหมี่เหลืองทอดกรอบ | deep fried pork dumpling wrapped with egg-noodles, served with plum sauce',
				price: 220, // Price assumed
				image: '/images/menu/1/STARTERS - Moo-Srong.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'กุ้งสไบ',
				name_en: 'Goong Sabai',
				description: 'กุ้งหมักห่มด้วยเส้นหมี่เหลืองทอดกรอบ | deep fried shrimp wrapped with egg-noodles served with plum sauce',
				price: 240, // Price assumed
				image: '/images/menu/1/STARTERS - Goong Sabai.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'เนื้อแดดเดียวสมุนไพรกรอบ',
				name_en: 'Nua Dad Diew',
				description: 'เนื้อแดดเดียวคั่วสมุนไพรกรอบ | sun-dry beef, stir-fry with chilli and topped with crispy Thai basil',
				price: 280, // Price assumed
				image: '/images/menu/1/STARTERS - Nua Dad Diew.avif',
				special_ingredient: "Mild"
			},
			{
				name_th: 'พล่าเนื้อตะใคร้หอม',
				name_en: 'Pla Nua Ta Crai Hom',
				description: 'พล่าเนื้อย่างรสจัด | spicy beef salad with lemongrass and mint',
				price: 290, // Price assumed
				image: '/images/menu/1/STARTERS - Pla Nua Ta Crai Hom.avif',
				special_ingredient: "ExtraHot"
			},
			{
				name_th: 'พิคานย่าหมักลาบ',
				name_en: 'Crying Tiger',
				description: 'Grilled (picanha - 170g.) beef E-sarn style with jaew sauce | Farmer certified 100% Angus Grain fed 120 days',
				price: 450,
				image: '/images/menu/1/STARTERS - Crying Tiger.avif',
				special_ingredient: 'Mild'
			},
			{
				name_th: 'ดาหลาม้าฮ่อ',
				name_en: 'Darha Ma hor',
				description: 'pineapple slide serve with nutty, Darha flower and mushroom',
				price: 210,
				image: '/images/menu/1/STARTERS - Darha Ma hor.avif',
				special_ingredient: 'Vegetarian'
			},
			{
				name_th: 'ยำดอกดาหลา',
				name_en: 'Yum Dok Darha',
				description: 'refreshing spicy Darha flower salad',
				price: 210,
				image: '/images/menu/1/STARTERS - Yum Dok Darha.avif',
				special_ingredient: 'Vegetarian, Mild'
			},
			{
				name_th: 'ลาบทอด',
				name_en: 'Larb Tod',
				description: 'deep fried spicy plant base ball [E-sarn flaver]',
				price: 210,
				image: '/images/menu/1/STARTERS - Larb Tod.avif',
				special_ingredient: 'Vegetarian, Hot'
			},
			{
				name_th: 'ตำสายบัว กุ้งสด/กุ้งสุก',
				name_en: 'Som Tum Sai Bua',
				description: 'ตำสายบัวไทยใส่กุ้ง หรือ ตำสายบัวกุ้งสดใส่ปลาร้า | stem of lotus flower made into spicy Thai salad',
				price: 210,
				image: '/images/menu/1/STARTERS - Som Tum Sai Bua.avif',
				special_ingredient: 'Hot'
			}
		],
		grilled: [
			{
				name_th: 'เก้าย่าง',
				name_en: 'Kao Yang (grilled platter - 9 sticks)',
				description: 'รวมของย่าง 9 ไม้',
				price: 450, // Price assumed
				image: '/images/menu/2/GRILLED - Kao Yang grilled platter - 9 sticks.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ไก่ย่างขมิ้น',
				name_en: 'Kai Yang Kamin',
				description: 'cumin marinated grilled chicken served with tamarind sauce',
				price: 250, // Price assumed
				image: '/images/menu/2/GRILLED - Kai Yang Kamin.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'กุ้งย่างตะไคร้',
				name_en: 'Goong Yang',
				description: 'grilled lemongrass shrimp with - 3 sticks',
				price: 280, // Price assumed
				image: '/images/menu/2/GRILLED - Goong Yang.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ตับไก่ย่าง',
				name_en: 'Tub Kai Yang',
				description: 'grilled chicken liver served with tamarind sauce',
				price: 180, // Price assumed
				image: '/images/menu/2/GRILLED - Tub Kai Yang.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ไส้กรอกขวัญ',
				name_en: 'Sai Krok Kwan',
				description: 'grilled Thai sour E-sarn sausage',
				price: 220, // Price assumed
				image: '/images/menu/2/GRILLED - Sai Krok Kwan.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'เนื้อย่างเตาถ่าน',
				name_en: 'Charcoal Grill',
				description: 'เนื้อส่วนพิคานย่า',
				price: 450, // Price assumed
				image: '/images/menu/2/GRILLED - Charcoal Grill.avif',
				special_ingredient: undefined
			}
		],
		'main-dish': [
			{
				name_th: 'ผัดไทยเทพฯกุ้งกระบอก',
				name_en: 'Pad Thai Tep',
				description: 'Sukhothai recipe Pad Thai with shrimp, *contain nuts',
				price: 230,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Pad Thai Tep.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ข้าวเนื้อแดดเดียวกะเพรากรอบ',
				name_en: 'Khao Nua Dad Diew',
				description: 'spicy fried rice with sun-dry beef, topped with crispy Thai basil',
				price: 260,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Khao Nua Dad Diew.avif',
				special_ingredient: 'Mild'
			},
			{
				name_th: 'ข้าวคั่วไส้กรอกขวัญ',
				name_en: 'Khao Kua Sai Krok Kwan',
				description: 'fried rice with sour E-sarn sausage',
				price: 210,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Khao Kua Sai Krok Kwan.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ข้าวคั่วตับทอดกระเทียม',
				name_en: 'Khao Kua Tub Tod Kra Tiam',
				description: 'fried rice with chicken liver and crispy garlic',
				price: 210,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Khao Kua Tub Tod Kra Tiam.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ข้าวคั่วปลาทูสมุนไพร',
				name_en: 'Khao Kua Pla Tu',
				description: 'fried rice with Thai Mackerel and herbs',
				price: 210,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Khao Kua Pla Tu.avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ผัดไทเทพฯ เต้าหู้ กระบอก',
				name_en: 'Pad Tai Tofu',
				description: 'Sukhothai recipe Pad Thai with tofu, *contain nuts',
				price: 230,
				image: '/images/menu/3/MAIN_DISH_IN_BAMBOO_TUBE - Pad Tai Tofu.avif',
				special_ingredient: 'Vegetarian'
			}
		],
		'plant-base': [
			{
				name_th: 'ดาหลาม้าฮ่อ',
				name_en: 'Darha Ma hor',
				description: 'pineapple slide serve with nutty, Darha flower and mushroom',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Darha Ma hor.avif',
				special_ingredient: 'Vegetarian'
			},
			{
				name_th: 'ยำดอกดาหลา',
				name_en: 'Yum Dok Darha',
				description: 'refreshing spicy Darha flower salad',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Yum Dok Darha.avif',
				special_ingredient: 'Vegetarian, Mild'
			},
			{
				name_th: 'ลาบทอด',
				name_en: 'Larb Tod',
				description: 'deep fried spicy plant base ball [E-sarn flaver]',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Larb Tod.avif',
				special_ingredient: 'Vegetarian, Hot'
			},
			{
				name_th: 'ผัดไทเทพฯ เต้าหู้ กระบอก',
				name_en: 'Pad Tai Tofu',
				description: 'Sukhothai recipe Pad Thai with tofu, *contain nuts',
				price: 230,
				image: '/images/menu/4/PLANT_BASE - Pad Tai Tofu.avif',
				special_ingredient: 'Vegetarian'
			},
			{
				name_th: 'ข้าวคั่วกระเพราหมูกรอบกระบอก',
				name_en: 'Khao Kua Kra Prao Mu Krob',
				description: 'spicy basil fried rice with crispy plant base',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Khao Kua Kra Prao Mu Krob.avif',
				special_ingredient: 'Vegetarian, Mild'
			},
			{
				name_th: 'ยำแหนมหมูกรอบทิพย์',
				name_en: 'Yum Nham Moo Krob',
				description: 'spicy sour fermented crispy plant base salad with fresh ginger, chilli, black sesame',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Yum Nham Moo Krob.avif',
				special_ingredient: 'Vegetarian, Mild'
			},
			{
				name_th: 'ลาบหมูกรอบทิพย์',
				name_en: 'Larb Moo Krob',
				description: 'deep fried spicy crispy plant base, seasoned with E-sarn flaver',
				price: 210,
				image: '/images/menu/4/PLANT_BASE - Larb Moo Krob.avif',
				special_ingredient: 'Vegetarian, Mild'
			}
		],
		'signature-drinks': [
			{
				name_th: 'สุราสมุนไพรเซท',
				name_en: 'Thai Herbal Liquor',
				description: 'รวม 3 ตัว เสิร์ฟครบชุด (พระอภัยมณี / ราชสีห์คำราม / กากี) | a taster set of 3 kinds',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - Thai Herbal Liquor.avif',
				special_ingredient: undefined,
				type: 'Type 1'
			},
			{
				name_th: 'สงกรานต์',
				name_en: 'SongKran',
				description: 'เปรี้ยว หวาน ดื่มง่าย ชวนให้สดชื่น | passionfruit, lime, syrup, mint',
				price: 330,
				image: '/images/menu/5/SIGNATURE_DRINKS - SongKran.avif',
				special_ingredient: 'Vegetarian',
				type: 'Type 1'
			},
			{
				name_th: 'บั้งไฟพญานาค',
				name_en: 'E-Sarn Rocket',
				description: 'สุราสมุนไพรทิ้งดิ่งลงในกระบอกไม้ไผ่ที่เต็มไปด้วยเบียร์ไทย | beer bomb with herbal liquor shot',
				price: 330,
				image: '/images/menu/5/SIGNATURE_DRINKS - E-Sarn Rocket.avif',
				special_ingredient: undefined,
				type: 'Type 1'
			},
			{
				name_th: 'ลอยกระทง',
				name_en: 'LOY KRA TONG',
				description: 'ลอยละล่อง แรง แต่ดื่มลื่น | Campari, syrup, egg white, flower pollen-infused liquor, dry vermouth, lime',
				price: 500,
				image: '/images/menu/5/SIGNATURE_DRINKS - LOY KRA TONG.avif',
				special_ingredient: undefined,
				type: 'Type 1'
			},
			{
				name_th: 'สยามสามช่า',
				name_en: 'SIAM SAMCHA [MICHELIN GALA DINNER 2023]',
				description: 'รางวัลรองชนะเลิศ Mekhong The Spirit Competition 2022 และเสริฟในงาน MICHELIN GALA DINNER 2023 | Mekhong, fire Samkler brown sugar, Samkler cordial, Aperol, sparkling rose',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - SIAM SAMCHA [MICHELIN GALA DINNER 2023].avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'แม่โขงเฉลิมไทย',
				name_en: 'Mekhong Chalerm Thai [MICHELIN GALA DINNER 2022]',
				description: 'แม่โขงเฉลิมไทย ถูกรับเชิญให้เสริฟในงาน MICHELIN GALA DINNER 2022 | Mekhong, Indian gooseberry, clove, kaffir leaves, fever tree tonic',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - Mekhong Chalerm Thai [MICHELIN GALA DINNER 2022].avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'ทอง',
				name_en: 'THONG [ MICHELIN GALA DINNER 2018 ]',
				description: 'ถูกคัดเลือกให้เสริฟในงาน Gala Michelin 2018 หอมหวานด้วยรสมะม่วงนำ้ดอกไม้ และน้ำผึ้งป่า | fresh mango, wild honey, dill, lime, syrup, egg white, pure gold leaf',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - THONG [ MICHELIN GALA DINNER 2018 ].avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'สว่างฟ้า',
				name_en: 'SA WANG FAH',
				description: 'จิน ดองเก็กฮวยป่า ชาหอมหมื่นลี้ บ๊วย และผสมด้วยโทนิคชั้นดี | local gin infused with; plum, herbs, chrysanthemum tea, Fever Tree tonic',
				price: 420,
				image: '/images/menu/5/SIGNATURE_DRINKS - SA WANG FAH.avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'เดินอากาศ',
				name_en: 'DERN AR-KAD',
				description: '2 รส ว็อดก้า รัม พริก-เกลือหิมาลายัน และสับปะรดรัม | rum, vodka, sweet & sour rimmed-glass, syrup, lime and pineapple',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - DERN AR-KAD.avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'ยามเย็น',
				name_en: 'YAM YEN',
				description: 'สดชื่น เด่นด้วยกลิ่นนำ้มันหอมระเหยจากใบโหระพา | crushed basil leaves, lime, syrup, Angostura bitter',
				price: 300,
				image: '/images/menu/5/SIGNATURE_DRINKS - YAM YEN.avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'ซ่อนอารมณ์',
				name_en: 'HIDDEN AGENDA',
				description: 'หวานซ่อนเปรี้ยว ใช้ผลไม้ตามฤดูกาล | sweet & sour taste of seasonal fruits of Thailand',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - HIDDEN AGENDA.avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'ชมดง',
				name_en: 'CHOM DONG',
				description: 'ชงแบบนิโกรนี่ ขิงตัดกับรสหวานจากอินทผาลัม และน้ำยาอุทัยทิพย์ | Negroni style cocktail with ginger, dates fruit, Campari, sweet vermouth, Thai bitter',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - CHOM DONG.avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'กาลครั้งหนึ่ง',
				name_en: 'KAL LA KRANG 1',
				description: 'จินล้ำลึก ชวนหวนคิดถึงอดีต หวานปนขม | dry gin, lime, butterfly pea and lime candy',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - KAL LA KRANG 1.avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'เอิบอันดามัน',
				name_en: 'ERB ANDAMAN',
				description: 'พาลงใต้ชมดงดอกดาหลา สาวงามที่โอบล้อมทะเลอันดามัน | Saneha craft gin, Darha cordiel, lime, Fever Tree tonic',
				price: 400,
				image: '/images/menu/5/SIGNATURE_DRINKS - ERB ANDAMAN.avif',
				special_ingredient: undefined,
				type: 'Type 2'
			},
			{
				name_th: 'HIGHBALL - เตยหอม',
				name_en: 'PANDAN',
				description: '(rum + pandan infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - HIGHBALL_PANDAN.avif',
				special_ingredient: undefined,
				type: '(local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'HIGHBALL - สับปะรด',
				name_en: 'PINEAPPLE',
				description: '(rum + soda + pineapple infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - HIGHBALL_PINEAPPLE.avif',
				special_ingredient: undefined,
				type: '(local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'HIGHBALL - บ๊วย',
				name_en: 'Plum',
				description: '(rum + plum infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - HIGHBALL_Plum.avif',
				special_ingredient: undefined,
				type: '(local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'ชาไทย',
				name_en: 'THAI TEA',
				description: '(rum + soda + Thai tea infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - THAI TEA.avif',
				special_ingredient: undefined,
				type: '(local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'อุทัยทิพย์',
				name_en: 'UTAITIP',
				description: '(rum + soda + Thai herbal bitter infused home-made syrup)',
				price: 380,
				image: '/images/menu/5/SIGNATURE_DRINKS - UTAITIP.avif',
				special_ingredient: undefined,
				type: '(local aged rum cocktails, low-ABV, highball)'
			},
			{
				name_th: 'สุราชุมชน',
				name_en: 'Local Distilled Spirits',
				description: 'สุรากลั่นชุมชนรสชาติดีทั่วไทย สอบถามได้จากพนักงาน (ซอต/แก้ว) | A curated selection of premium Thai craft spirits',
				price: 350,
				image: '/images/menu/product-placeholder.avif',
				special_ingredient: undefined,
				type: 'Type 4'
			},
			{
				name_th: 'อุ มิกซ์เบียร์/ซอฟดริงค์',
				name_en: 'Au Mixed',
				description: 'เลือกเสิร์ฟกับ เบียร์ หรือซอฟดริ้ง | local rice wine from E-Sarn, served with beer or soft drinks',
				price: 290,
				image: '/images/menu/5/SIGNATURE_DRINKS - Au Mixed.avif',
				special_ingredient: undefined,
				type: 'Type 4'
			},
			{
				name_th: 'สาโทเมืองแพร่',
				name_en: 'Sato Phrae',
				description: 'สาโทจากข้าว 5 สายพันธุ์ อาทิ ข้าวเหนียวแม่โจ้ กข6 | Local rice wine made from 5 types of sticky rice [Phrae: North of TH] Alc.9.1%',
				price: 290,
				image: '/images/menu/5/SIGNATURE_DRINKS - Sato Phrae.avif',
				special_ingredient: undefined,
				type: 'Type 4'
			},
			{
				name_th: 'สาโทเทพนม',
				name_en: 'DEVANOM CRAFT SATO',
				description: 'คราฟท์สาโทพรีเมี่ยมรสนุ่มนวลทำจากข้าวเหนียวเขี้ยวงูเชียงราย | Premium sato crafted with care using the finest Khiew Ngu sticky rice from Chiangrai. aromatic, fruity note, ALC.6%',
				price: 290,
				image: '/images/menu/5/SIGNATURE_DRINKS - DEVANOM CRAFT SATO.avif',
				special_ingredient: undefined,
				type: 'Type 4'
			},
			{
				name_th: 'รวงข้าว สยามแซฟไฟร์',
				name_en: 'RUANG KHAO SIAM SAPPHIRE',
				description: 'Aged in oak casks, imparting a rich, full-bodied, and aromatic flavor. On the rock or neat',
				price: 450,
				image: '/images/menu/5/SIGNATURE_DRINKS - RUANG KHAO SIAM SAPPHIRE.avif',
				special_ingredient: undefined,
				type: 'Type 4'
			},
			{
				name_th: 'สุราขาวสักทองแพร่',
				name_en: 'Lao Khao',
				description: 'สุราขาวบ่มพิเศษ 35 ดีกรี ดื่มเป็นช็อตหรือสูตรผสมกระทิงแดง | Thai white spirit, strong sensation. Alc. 35%',
				price: 350,
				image: '/images/menu/5/SIGNATURE_DRINKS - Lao Khao.avif',
				special_ingredient: undefined,
				type: 'Type 4'
			},
			{
				name_th: 'แสงโสม + มิกซ์เซอร์',
				name_en: 'LOCAL RUM + MIXER',
				description: '',
				price: 350,
				image: '/images/menu/product-placeholder.avif',
				special_ingredient: undefined,
				type: 'Type 5'
			},
			{
				name_th: 'จิน โทนิค',
				name_en: 'GIN + TONIC',
				description: 'ราคา 400 - 1,000 บาท',
				price: 400,
				image: '/images/menu/product-placeholder.avif',
				special_ingredient: undefined,
				type: 'Type 5'
			},
			{
				name_th: 'จินไทย โทนิค',
				name_en: 'THAI GIN + TONIC',
				description: 'We use Fever Tree Tonic, and Iron Balls Gin',
				price: 450,
				image: '/images/menu/5/SIGNATURE_DRINKS - THAI GIN+ TONIC.avif',
				special_ingredient: undefined,
				type: 'Type 5'
			},
			{
				name_th: 'วิสกี้ เบอร์เบิ้น วอดก้า + มิกซ์เซอร์',
				name_en: 'SCOTH WHISKY / VODKA / BOURBON / + MIXER',
				description: 'ราคา 400-1,000 บาท',
				price: 400,
				image: '/images/menu/product-placeholder.avif',
				special_ingredient: undefined,
				type: 'Type 5'
			},
			{
				name_th: 'วิสกี้แบบซิงเกิ้ลมอลท์',
				name_en: 'SINGLE MALT WHISKY',
				description: 'เสิร์ฟกับน้ำแข็งมวลแน่น ใสบริสุทธิ์ | by shot, on the rock or neat, we use high quality rock ice',
				price: 400,
				image: '/images/menu/product-placeholder.avif',
				special_ingredient: undefined,
				type: 'Type 5'
			},
			{
				name_th: 'น้ําแร่',
				name_en: 'MINERAL WATER',
				description: '(Sai Yok Springs still water - 250 ml.)',
				price: 50,
				image: '/images/menu/5/SIGNATURE_DRINKS - MINERAL WATER.avif',
				special_ingredient: undefined,
				type: 'Type 6'
			},
			{
				name_th: 'น้ําแร่มีฟอง',
				name_en: 'SPARKLING WATER',
				description: 'Sai Yok Springs sparkling water - 250 ml',
				price: 120,
				image: '/images/menu/5/SIGNATURE_DRINKS - SPARKLING WATER.avif',
				special_ingredient: undefined,
				type: 'Type 6'
			},
			{
				name_th: 'น้ำเกสรดอกมะพร้าว',
				name_en: 'COCONUT PILLEN FLOWER',
				description: 'ของดีจากแม่กลอง ความหวานจากธรรมชาติ สดชื่น สุดฟิน | Non-alcoholic',
				price: 210,
				image: '/images/menu/5/SIGNATURE_DRINKS - COCONUT PILLEN FLOWER.avif',
				special_ingredient: 'Vegetarian',
				type: 'Type 6'
			},
			{
				name_th: 'เปิดบริสุทธ์',
				name_en: 'Like A Virgin',
				description: 'ตะไคร้ ใบเตย | lemongrass and pandan syrup, lime',
				price: 230,
				image: '/images/menu/5/SIGNATURE_DRINKS - Like A Virgin.avif',
				special_ingredient: 'Vegetarian',
				type: 'Type 6'
			},
			{
				name_th: 'โทนิคฟีเวอร์ทรี',
				name_en: 'Fever Tree Tonic',
				description: '',
				price: 150,
				image: '/images/menu/5/SIGNATURE_DRINKS - Fever Tree Tonic.avif',
				special_ingredient: undefined,
				type: 'Type 6'
			},
			{
				name_th: 'โซดา น้ำอัดลม',
				name_en: 'Soft drinks',
				description: 'โค้ก / สไปรท์ / โซดา | Coke / Sprite / Soda',
				price: 100,
				image: '/images/menu/5/SIGNATURE_DRINKS - Soft drinks.avif',
				special_ingredient: undefined,
				type: 'Type 6'
			}
		],
		'beer-wine': [
			{
				name_th: 'MAKMAO WINE (Red)',
				name_en: 'MAKMAO WINE (Red)',
				description: 'ไวน์แดง ไทย (สกลนคร), Mak Mao berry; เบอร์รี่และผลไม้สด | Red wine, Thailand (Sakon Nakhon); organic Mak Mao berry – fresh fruit notes & berry',
				price: 1400,
				image: '/images/menu/6/BEER_WINE - MAKMAO WINE (Red).avif',
				special_ingredient: undefined
			},
			{
				name_th: 'THONGKHAM ESTATE (Red)',
				name_en: 'THONGKham ESTATE (Red)',
				description: 'ไวน์แดงไทย (เชียงราย)ทองคำ เอสเตท ปิโนต์ นัวร์ 2022 — เชอร์รี่ ราสเบอร์รี่ วานิลลา โอ๊ค | Red Wine Thailand (Chiang Rai) Thongkham Estate Pinot Noir 2022',
				price: 1500,
				image: '/images/menu/6/BEER_WINE - THONGKHAM ESTATE (Red).avif',
				special_ingredient: undefined
			},
			{
				name_th: 'GRANMONTE SAKUNA (Rosé)',
				name_en: 'GRANMONTE SAKUNA (Rosé)',
				description: 'ไวน์โรเซ่ไทย (เขาใหญ่)กรามอนเต้ สกุณา โรเซ่ — สีชมพูใสเบอร์รี่ รสนุ่ม หวานบาง สดชื่น | Rosé Wine Thailand (Khao Yai) GranMonte Sakuna Rosé',
				price: 1500,
				image: '/images/menu/6/BEER_WINE - GRANMONTE SAKUNA (Rosé).avif',
				special_ingredient: undefined
			},
			{
				name_th: 'LAMADOR (Red)',
				name_en: 'LAMADOR (Red)',
				description: 'ไวน์แดง ชิลี, Merlot 2019; ผลไม้แดง & ดอกไวโอเล็ต | Red wine, Chile; Merlot 2019 – red fruit & violet floral notes',
				price: 1500,
				image: '/images/menu/6/BEER_WINE - LAMADOR (Red).avif',
				special_ingredient: undefined
			},
			{
				name_th: 'FINIMONDO (Red)',
				name_en: 'FINIMONDO (Red)',
				description: 'ไวน์แดง อิตาลี, Nero d’Avola & Syrah; เบอร์รี่ ยาสูบ เครื่องเทศ | Red wine, Italy; Nero d’Avola & Syrah – intense berry, tobacco & spice',
				price: 2000,
				image: '/images/menu/6/BEER_WINE - FINIMONDO (Red).avif',
				special_ingredient: undefined
			},
			{
				name_th: 'GRANMONTE VIOGNIER (White)',
				name_en: 'GRANMONTE VIOGNIER (White)',
				description: 'ไวน์ขาวไทย (เขาใหญ่)กรามอนเต้ วิอองเย่ 2024 — ดอกไม้เมืองร้อน แร่ธาตุ โอ๊ค | White Wine Thailand (Khao Yai) GranMonte Viognier 2024',
				price: 1500,
				image: '/images/menu/6/BEER_WINE - GRANMONTE VIOGNIER (White).avif',
				special_ingredient: undefined
			},
			{
				name_th: 'PÃ ROAD (White)',
				name_en: 'PÃ ROAD (White)',
				description: 'ไวน์ขาว นิวซีแลนด์ (Marlborough), Sauvignon Blanc 2023; ดอกไม้ ซิตรัส และเครื่องเทศ | White wine, New Zealand (Marlborough); Sauvignon Blanc 2023',
				price: 1800,
				image: '/images/menu/6/BEER_WINE - PÃ ROAD (White).avif',
				special_ingredient: undefined
			},
			{
				name_th: '7 CASINE (Sparkling)',
				name_en: '7 CASINE (Sparkling)',
				description: 'ไวน์ขาว อิตาลี, Prosecco DOC; เบา ดราย ฟองนุ่ม | White wine, Italy; Prosecco DOC – light, dry & fine bubbles',
				price: 1600,
				image: '/images/menu/6/BEER_WINE - 7 CASINE (Sparkling).avif',
				special_ingredient: undefined
			},
			{
				name_th: 'ชาละวัน',
				name_en: 'CHALAWAN BEER',
				description: '(PALE ALE) 4.7% ALC. (small bottle)',
				price: 280,
				image: '/images/menu/6/BEER_WINE - CHALAWAN BEER.avif',
				special_ingredient: undefined,
                type: "(local beer - bottle)"
			},
			{
				name_th: 'บุษบา',
				name_en: 'BUSSABA BEER',
				description: 'wheat Beer จากภูเก็ต',
				price: 280,
				image: '/images/menu/6/BEER_WINE - BUSSABA BEER.avif',
				special_ingredient: undefined,
                type: "(local beer - bottle)"
			},
			{
				name_th: 'สิงห์',
				name_en: 'SINGHA BEER',
				description: '(LAGER BEER) 5% ALC. (small bottle)',
				price: 250,
				image: '/images/menu/6/BEER_WINE - SINGHA BEER.avif',
				special_ingredient: undefined,
                type: "(local beer - bottle)"
			}
		],
		dessert: [
			{
				name_th: 'จินดามณี',
				name_en: 'CHINDA MANEE',
				description: 'ข้าวเหนียวมูน 3 หน้า มะม่วงน้ำดอกไม้ + กระฉีก มะพร้าวทึนทึก + ทองหยอดหยาดเพชร สูตรไข่เค็ม | Mango sticky rice with shredded coconut and baby Thong yod (eggdrop sweet)',
				price: 180,
				image: '/images/menu/7/DESSERT - CHINDA MANEE.avif',
				special_ingredient: undefined
			}
		]
	};

    // 2. สร้าง Object สำหรับเก็บข้อมูล SVG และ Tooltip
	const ingredientIcons: Record<string, { svg: string; text: string }> = {
		ExtraHot: {
            text: 'Extra hot',
            svg: `<svg xmlns="http://www.w3.org/2000/svg" data-bbox="1.806 1.21 18.369 19.79" viewBox="0 0 24 24" height="24" width="24" data-type="shape" class="injected-svg" data-src="https://static.wixstatic.com/shapes/ec845c_a046f8b157e54b5d888fc424a1dea027.svg" xmlns:xlink="http://www.w3.org/1999/xlink" role="img"><title>Extra hot</title><g><path d="M19.17 11.82c-.1-.07-.21-.13-.33-.17.28-.87.59-2.49-.15-4.47l-.94.35c.66 1.77.36 3.19.12 3.88h-.17c.24-1.5-.46-2.24-.97-2.58-.1-.06-.21-.12-.32-.17.28-.87.58-2.49-.16-4.46l-.94.35c.66 1.76.36 3.19.12 3.87-.06-.01-.11-.01-.17-.01.25-1.49-.45-2.23-.96-2.57-.1-.07-.21-.12-.33-.17.28-.87.58-2.49-.16-4.46l-.94.35c.66 1.76.36 3.19.12 3.87-.34-.02-.68.01-1 .12-.73.24-1.28.78-1.57 1.52 0 .01 0 .02-.01.02-.01.05-1.67 4.81-7.78 5.63-.44.07-.78.42-.82.87-.04.45.22.84.64.98.96.31 1.97.45 2.99.45 1.14 0 2.3-.18 3.39-.51-1.01.55-2.25 1-3.77 1.2-.44.07-.78.42-.82.87-.04.45.22.84.65.98.95.3 1.96.45 2.99.45 1.14 0 2.3-.18 3.39-.51-1.01.55-2.25 1-3.77 1.21-.44.06-.78.41-.82.86-.04.45.22.84.64.98.95.31 1.97.45 2.99.45 4.01 0 8.19-2.2 9.47-5.4.93-2.32.01-3.36-.62-3.77l.01-.01Zm-.31 3.4c-1.38 3.44-6.87 5.63-11 4.44 3.77-.57 5.95-2.49 7.14-4.06.53-.7.86-1.33 1.05-1.74 0-.01.01-.02.01-.03.11-.23.16-.38.18-.43.13-.33.31-.56.51-.7.15-.12.3-.19.43-.23l.24-.06c.42-.06.87.02 1.2.24.83.55.59 1.7.24 2.57ZM5.43 16.66c3.75-.57 5.93-2.48 7.11-4.04.86-1.13 1.21-2.08 1.26-2.22.23-.58.64-.82.95-.92l.24-.06c.41-.06.86.02 1.19.24.65.42.65 1.21.45 1.95-.61.27-1.08.77-1.33 1.44 0 0 0 .01-.01.02 0 .02-.29.83-1.04 1.84-2.34 1.76-5.92 2.59-8.82 1.75Zm-2.44-2.99c6.45-.98 8.26-5.92 8.38-6.26.22-.58.64-.82.94-.92.47-.15 1.04-.08 1.44.18.64.42.64 1.21.44 1.95-.61.28-1.07.78-1.32 1.43-.01.01-.01.02-.01.02-.03.08-.3.85-1 1.8-2.34 1.8-5.94 2.65-8.87 1.8Z"></path></g></svg>`
        },
        Hot: {
			text: 'Hot',
			svg: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M19.854 10.66c-.13-.09-.27-.16-.42-.22.32-.97.68-2.83-.16-5.09l-.94.35c.26.69.38 1.34.43 1.93l-.02 1.18c-.06.59-.18 1.08-.29 1.4-.1-.02-.2-.02-.3 0 .28-1.68-.5-2.5-1.07-2.87-.13-.09-.27-.16-.41-.22.32-.97.68-2.83-.16-5.09l-.94.35c.77 2.05.38 3.73.12 4.51-.39-.04-.78 0-1.16.12-.81.27-1.43.87-1.74 1.7v.02c-.08.22-1.95 5.51-8.92 6.45-.47.07-.83.45-.87.93-.04.47.23.89.68 1.04 1.08.35 2.23.51 3.39.51 1.38 0 2.78-.23 4.09-.66-1.19.69-2.68 1.26-4.52 1.51-.48.07-.84.45-.88.93-.04.47.23.89.68 1.04 1.08.34 2.23.51 3.39.51 4.54 0 9.26-2.49 10.71-6.1 1.04-2.61.02-3.76-.68-4.22l-.01-.01Zm-.25 3.84c-1.61 4.02-8.1 6.55-12.84 4.99 4.22-.57 6.73-2.63 8.14-4.39 1.1-1.38 1.53-2.56 1.59-2.72.26-.69.75-.98 1.12-1.1.09-.03.19-.05.28-.06.49-.09 1.01.01 1.41.28.99.64.71 1.99.3 3Zm-15.6 1.67c7.51-1.03 9.6-6.75 9.72-7.12.27-.69.76-.98 1.12-1.1.56-.18 1.22-.1 1.7.22.76.49.77 1.4.55 2.25-.72.29-1.26.85-1.54 1.61 0 0-.01.01-.01.02 0 .03-.37 1.06-1.34 2.3-2.76 2-6.9 2.9-10.2 1.82Z"></path></svg>`
		},
		Mild: {
			text: 'Mild',
			svg: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M18.76 8.52c-.16-.1-.33-.18-.51-.25.36-1.06.8-3.17-.16-5.75l-.94.35c.88 2.36.42 4.3.12 5.16-.45-.04-.9 0-1.33.13-.89.29-1.58.95-1.93 1.87v.02c-.09.25-2.2 6.23-10.08 7.3-.5.07-.89.47-.93.98-.04.51.25.95.73 1.11 1.21.39 2.49.57 3.79.57 5.08 0 10.36-2.79 11.98-6.82 1.16-2.88.03-4.16-.75-4.67h.01Zm-.18 4.29C16.76 17.36 9.42 20.22 4 18.42c0-.07.05-.08.07-.08 8.42-1.14 10.75-7.56 10.89-7.97.31-.8.88-1.13 1.3-1.27.65-.21 1.4-.12 1.96.25 1.15.75.83 2.29.36 3.46Z"></path></svg>`
		},
		Organic: { // เพิ่มไอคอนเผื่อไว้
			text: 'Organic',
			svg: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M12.5 3.5h-1v2h1v-2Zm0 17v-2h-1v2h1ZM5.639 6.378l.707-.707L7.76 7.085l-.707.707-1.414-1.414Zm11.307 9.893-.707.707 1.415 1.414.707-.707-1.415-1.414ZM3.5 11.5h2v1h-2v-1Zm17 0h-2v1h2v-1ZM6.341 18.387l-.707-.707 1.414-1.414.707.707-1.414 1.414ZM17.658 5.675 16.244 7.09l.707.708 1.414-1.415-.707-.707ZM7.5 12c0-2.48 2.02-4.5 4.5-4.5s4.5 2.02 4.5 4.5-2.02 4.5-4.5 4.5-4.5-2.02-4.5-4.5Zm1 0c0 1.93 1.57 3.5 3.5 3.5s3.5-1.57 3.5-3.5-1.57-3.5-3.5-3.5-3.5 1.57-3.5 3.5Z"></path></svg>`
		},
		Vegetarian: {
			text: 'Vegan',
			svg: `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M19.59 5.75a.504.504 0 0 0-.34-.34c-2.68-.77-5.52-.42-7.9.89-.65-1.4-1.72-2.55-3.13-3.24a.487.487 0 0 0-.44 0A6.722 6.722 0 0 0 4 9.12c0 1.84.77 3.6 2.1 4.87-.17 1.3-.09 2.65.24 3.96L4 20.29l.71.71 2.34-2.34c.85.22 1.72.34 2.58.34 2.71 0 5.36-1.06 7.33-3.03a10.4 10.4 0 0 0 2.63-10.22ZM5 9.12C5 7 6.14 5.09 8 4.07c1.12.61 2 1.61 2.51 2.77-.52.36-1.02.74-1.47 1.2a10.44 10.44 0 0 0-2.71 4.74A5.716 5.716 0 0 1 5 9.12Zm11.26 6.14c-2.2 2.2-5.34 3.13-8.36 2.56l5.66-5.66-.71-.71-5.67 5.67c-.57-3.03.35-6.17 2.56-8.37a9.35 9.35 0 0 1 8.96-2.44c.82 3.21-.1 6.62-2.44 8.96v-.01Z"></path></svg>`
		}
	};

	// --- Data (อัปเดตข้อมูล Header ที่นี่) ---
	const menuCategories: MenuCategory[] = [
		{
			value: 'starters',
			thai: 'ทานเล่น',
			english: 'STARTERS',
			sub_head: '(all prices are subject to 10% service charge and 7 % VAT)'
		},
		{
			value: 'grilled',
			thai: 'เตาถ่าน',
			english: 'GRILLED',
			sub_head: '(all prices are subject to 10% service charge and 7 % VAT)',
			description: '(using Thai earth stove)'
		},
		{
			value: 'main-dish',
			thai: 'อิ่มในกระบอก',
			english: 'MAIN DISHES',
			sub_head: '(all prices are subject to 10% service charge and 7 % VAT)'
		},
		{
			value: 'plant-base',
			thai: 'อาหารจากพืช',
			english: 'PLANT BASE',
			sub_head: '(all prices are subject to 10% service charge and 7 % VAT)'
		},
		{
			value: 'signature-drinks',
			thai: 'เครื่องดื่มเทพฯ',
			english: 'SIGNATURE DRINKS',
			sub_head: '(all prices are subject to 10% service charge and 7 % VAT)'
		},
		{
			value: 'beer-wine',
			thai: 'BEER & WINE',
			english: '',
			sub_head: '(all prices are subject to 10% service charge and 7 % VAT)',
			description: 'ค่าเปิดขวดไวน์ที่ลูกค้านํามาเอง 1,500++ / Wine corkage fee 1,500++'
		},
		{
			value: 'dessert',
			thai: 'ของหวานเทพฯ',
			english: 'DESSERT',
			sub_head: '(all prices are subject to 10% service charge and 7 % VAT)'
		}
	];

		// --- State ---
	let selectedCategoryValue = $state('starters');

	    // --- Configuration ---
	// 1. สร้าง Array สำหรับเก็บชื่อ Type ที่ไม่ต้องการให้แสดงเป็นหัวข้อ
	const EXCLUDED_GROUP_TITLES = ['ทั่วไป', 'Type 1', 'Type 2', 'Type 3', 'Type 4', 'Type 5', 'Type 6'];

    // --- Derived State ---
	// >> เพิ่มบรรทัดนี้เข้ามา <<
	let selectedCategory = $derived(menuCategories.find((cat) => cat.value === selectedCategoryValue));

	// --- Derived State (ทำให้ง่ายลง) ---
	let displayedItems = $derived(allMenuItems[selectedCategoryValue] ?? []);

	// --- Helper Function ---
	function groupItems(items: MenuItem[]): [string, MenuItem[]][] {
		if (!items.length) return [];
		const groups = new Map<string, MenuItem[]>();
		const defaultGroup = 'ทั่วไป';

		for (const item of items) {
			// ใช้ item.type ในการจัดกลุ่ม ถ้าไม่มีให้ใช้ defaultGroup
			const groupName = item.type ?? defaultGroup; 
			if (!groups.has(groupName)) {
				groups.set(groupName, []);
			}
			groups.get(groupName)!.push(item);
		}
		return Array.from(groups.entries());
	}
</script>

<svelte:head>
    <title>[Clone] Menu | TEP BAR</title>
</svelte:head>

<main style="place-self: center; padding: 1rem 0 1rem;">
    <section>
        <h2 style="text-align: center; font-weight: 100; font-size: 20px; margin: 10px 0;">Welcome to Tep Bar — Thailand’s Cultural Bar.</h2>
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

    {#if selectedCategory}
		<section class="category-header" style="margin: 2rem 0;">
			<h3 style="font-size: 1.55rem; font-weight: 100;">
				{menuCategories.findIndex((c) => c.value === selectedCategory.value) + 1})
				{selectedCategory.thai}
				{#if selectedCategory.english}| {selectedCategory.english}{/if}
			</h3>
			<p class="sub-head">{selectedCategory.sub_head}</p>
		</section>

        {#if selectedCategory.description}
			<div style="width: 100%; text-align: center; display: flex; justify-content: center; align-items: center; margin: 1rem 0; ">
				<p class="description-option">{selectedCategory.description}</p>
			</div>
		{/if}
        <hr>
	{/if}
	
	{#each groupItems(displayedItems) as [type, itemsInGroup], groupIndex}
		{@const showTitle = !EXCLUDED_GROUP_TITLES.includes(type)}
		{@const showDivider = groupIndex > 0}

		{#if showTitle || showDivider}
			<div class="group-header" style="margin-top: 3rem;">
				{#if showTitle}
					<h4 class="group-title">{type}</h4>
				{/if}
				{#if showDivider}
					<hr class="group-divider" />
				{/if}
			</div>
		{/if}

		<div class="menu-container">
			{#each itemsInGroup as item}
				<div class="menu-card">
					<div>
						<img src={item.image} alt={item.name_th} />
						<h5 style="font-size: 18px; font-weight: 100;">
							★ {item.name_th} | {item.name_en}
						</h5>
					</div>
					<div>
						<p style="font-size: 15px;">{item.description}</p>
					</div>

					<div style=" display: flex; flex-direction: column; gap: 10px;">
                        <div class="ingredients-wrapper">
                            {#if item.special_ingredient}
                                {#each item.special_ingredient.split(', ') as ingredient}
                                    {@const iconInfo = ingredientIcons[ingredient.trim()]}
                                    {#if iconInfo}
                                        <Icon
                                            iconData={iconInfo.svg}
                                            tooltipText={iconInfo.text}
                                        />
                                    {/if}
                                {/each}
                            {/if}
                        </div>

                        <p style="font-size: 18px;">฿{item.price}</p>
					</div>
				</div>
			{/each}
		</div>
	{/each}

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
        width: 750px;
        font-weight: 200;
    }
    .menu-card {
        border-radius: 8px;
        padding: 0.51rem;
        text-align: center;
        line-height: 2rem;
        display: flex;
        flex-direction: column;
        justify-content: start;
        gap: 10px;
    }

    .menu-card img {
        width: 100%;
        aspect-ratio: 1 / 1; /* ทำให้รูปเป็นสี่เหลี่ยมจัตุรัส */
        object-fit: cover;
        border-radius: 4px;
    }
    /* menu card */

    /* ... css อื่นๆ ... */

    .group-header {
        text-align: center; /* ทำให้ h4 และ hr อยู่ตรงกลาง */
    }

    .group-title {
		font-weight: 200;
        margin-bottom: 1rem; /* ระยะห่างใต้หัวข้อ */
	}

	.group-divider {
		border: none;
		border-top: 1px solid #333;
        margin: 1rem auto 1rem; /* จัดกลางและกำหนดระยะห่าง */
	}

    /* ... css อื่นๆ ... */

    .ingredients-wrapper {
        display: flex;
        justify-content: center;
        gap: 8px; /* ระยะห่างระหว่างไอคอน */
        margin-top: auto; /* ดันให้ไอคอนอยู่เหนือราคาเสมอ */
        /* padding: 0.5rem 0; */
    }

    .category-header {
        place-self: center;
        text-align: center;
    }

	.description-option {
		font-size: 1.1rem; width: 300px;
	}

    @media (max-width: 768px) {
        .menu-container {
            grid-template-columns: 1fr; /* 👈 ยังคงเป็น 1 คอลัมน์ */
            width: 90%; /* 👈 กำหนดความกว้างของ container ให้เล็กลง (เช่น 90% ของหน้าจอ) */
            max-width: 250px; /* 👈 (แนะนำ) กำหนดความกว้างสูงสุดเพื่อไม่ให้ใหญ่เกินไป */
            margin: 0 auto; /* 👈 จัด container ให้อยู่กึ่งกลาง */
        }
    }

	@media (max-width: 425px) {
		.description-option {
			width: 300px;
		}
	}
</style>