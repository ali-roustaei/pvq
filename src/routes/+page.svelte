<script lang="ts">
	import { Button, Radio } from 'flowbite-svelte';

	const options = [
		{ value: 1, label: 'اصلاً شبیه من نیست' },
		{ value: 2, label: 'شبیه من نیست' },
		{ value: 3, label: 'خیلی کم شبیه من است' },
		{ value: 4, label: 'تا حدی شبیه من است' },
		{ value: 5, label: 'شبیه من است' },
		{ value: 6, label: 'خیلی شبیه من است' }
	];

	const QUESTIONS = [
		"فکر کردن به ایده‌های جدید و خلاق بودن برایش مهم است. او دوست دارد هر کاری را به سبک ویژه و تازه‌ی خودش انجام دهد.",
		"ثروتمند بودن برای او مهم است. دوست دارد پول و وسایل قیمتی فراوانی داشته باشد.",
		"مهم است که با همه‌ی انسان‌ها در جهان، به شکل برابر برخورد شود. همه باید فرصت‌های برابر داشته باشند.",
		"برایش مهم است که توانمندی‌هایش را نشان دهد و مردم او را به خاطر چیزی که هست، تحسین کنند.",
		"برایش مهم است که در یک محیط امن زندگی کند و از هر چیزی که امنیتش را به خطر بیاندازد دوری می‌کند.",
		"او فکر می‌کند که مهم است در زندگی فعالیت‌های متنوعی انجام دهد. همیشه دنبال چیز تازه‌ای است که آن را امتحان کند.",
		"فکر می‌کند که انسان‌ها باید همان‌کاری را که به آن‌ها گفته می‌شود انجام دهند. او فکر می‌کند که باید قانون را همیشه رعایت کرد؛ حتی وقتی هیچ‌کس نمی‌بیند و خبردار نمی‌شود.",
		"برایش مهم است که به حرف آن‌هایی که مثل خودش فکر نمی‌کنند گوش بدهد. حتی وقتی با آن‌ها مخالف است، می‌کوشد آن‌ها را درک کند.",
		"فکر می‌کند مهم است که بیشتر از آن‌چه داری نخواهی. او باور دارد که انسان‌ها باید به آن‌چه دارند راضی باشند.",
		"از هر فرصتی که برای تفریح کردن دست دهد‌ استفاده می‌کند. برایش مهم است کارهایی انجام دهد که برایش لذت‌بخش باشند.",
		"برایش مهم است که درباره‌ی آن‌چه انجام می‌دهد خودش تصمیم بگیرد. دوست دارد در فعالیت‌ها و برنامه‌ریزی‌هایش آزاد باشد.",
		"برایش بسیار مهم است که به اطرافیانش کمک کند. می‌خواهد مراقب صحت و سلامت آن‌ها باشد.",
		"برایش مهم است که بسیار موفق باشد. دوست دارد که دیگران را تحت تأثیر قرار دهد.",
		"برایش بسیار مهم است که کشورش امنیت داشته باشد. او معتقد است که دولت باید مراقب تمام تهدید‌هایی که از داخل یا خارج به وجود می‌آیند باشد.",
		"ریسک کردن را دوست دارد. او همیشه در پی ماجراجویی است.",
		"برایش مهم است که همیشه درست رفتار کند. او از انجام هر کاری که مردم بگویند اشتباه است اجتناب می‌کند.",
		"مسئول بودن و این‌که به دیگران امر و نهی کند برایش مهم است. او می‌خواهد دیگران کارهایی را که او می‌گوید انجام دهند.",
		"وفاداری به دوستان برایش مهم است. او خودش را وقف دوستان نزدیکش می‌کند.",
		"به شدت معتقد است که انسان‌ها باید مراقب طبیعت باشند. حفظ محیط زیست برایش مهم است.",
		"باورهای دینی برایش مهم است. او در رعایت اصول و فرائض مذهبی کوشا و جدی است.",
		"برایش تمیز و منظم بودن همه‌چیز مهم است. واقعاً دوست ندارد جایی به‌هم‌ریخته باشد.",
		"فکر می‌کند علاقه‌داشتن به اطراف و کنجکاوی نسبت به محیط مهم است. او سعی می‌کند از هر چیزی سر در بیاورد.",
		"او فکر می‌کند که انسان‌ها در جهان باید در صلح و هماهنگی با یکدیگر زندگی کنند. ترویج صلح میان همه‌ی گروه‌ها در جهان برای او اهمیت دارد.",
		"فکر می‌کند بلندپروازی خیلی مهم است. او دوست دارد نشان دهد که چقدر توانمند است.",
		"او فکر می‌کند بهتر است هر کاری به روش سنتی‌اش انجام شود. برایش مهم است که سنت‌هایی را که آموخته است رعایت کند.",
		"کیف کردن و لذت بردن از لذت‌های زندگی برایش مهم است. دوست دارد افراط کند و تا ته هر لذتی برود.",
		"دوست دارد به نیازهای دیگران پاسخ داده و آن‌ها را تأمین کند. سعی می‌کند از تمام کسانی که می‌شناسد حمایت کند.",
		"او باور دارد که همیشه باید به پدر و مادر و افراد مسن احترام بگذارد. حرف‌گوش‌کن بودن در برابر آن‌ها برایش مهم است.",
		"دوست دارد با همه – حتی کسانی که او نمی‌شناسد – منصفانه برخورد شود. حمایت از ضعفا در جامعه برایش اهمیت دارد.",
		"او سورپرایز شدن را دوست دارد. برایش مهم است که زندگی‌اش هیجان‌انگیز باشد.",
		"به شدت مراقب است که مریض نشود. حفظ سلامتی برایش بسیار مهم است.",
		"جلو زدن و پیشی گرفتن در زندگی برایش مهم است. او همیشه می‌کوشد تا بهتر از دیگران باشد.",
		"برایش مهم است کسانی را که به او آسیب زده‌اند ببخشد. سعی می‌کند خوبی‌های آن‌ افراد را ببیند و کینه به دل نگیرد.",
		"استقلال برایش مهم است. دوست دارد به خودش تکیه کند.",
		"وجود یک دولت با ثبات برایش مهم است. برایش مهم است که نظم اجتماعی حفظ شود.",
		"برایش مهم است که همیشه و همه‌جا با دیگران مودب برخورد کند. می‌کوشد که دیگران را آشفته و آزرده نکند.",
		"واقعاً دوست دارد از زندگی لذت ببرد. برایش مهم است که اوقات خوشی داشته باشد.",
		"برایش مهم است که متواضع و فروتن باشد. مراقب است که توجه‌ها را به خودش جلب نکند.",
		"دوست دارد همیشه او آن فردی باشد که تصمیم نهایی را می‌گیرد. رهبر جمع بودن برایش مهم است.",
		"برایش مهم است که خود را با طبیعت تطبیق دهد. او باور دارد که انسان‌ها نباید طبیعت را تغییر دهند."
	];

	interface TopicInfo {
		description: string; // جمله‌ی کوتاه زیر عنوان
		definition: string; // تعریف رسمی شوارتز
		dimension: string; // دسته‌ی کلان (ابعاد مرتبه‌ی بالاتر)
		alt: string[]; // ترجمه‌های دیگر
		details: string[]; // متن «بیشتر بخوانید»
	}

	const TOPIC_INFO: Record<string, TopicInfo> = {
		Hedonism: {
			description: 'میزان اهمیت لذت، خوشی و تجربه‌های لذت‌بخش برای شما.',
			definition: 'لذت و ارضای حسی برای خود فرد.',
			dimension: 'گشودگی به تغییر و خودافزایی (این ارزش در مرز هر دو دسته است)',
			alt: ['خوش‌گذرانی', 'خوشی‌طلبی'],
			details: [
				'لذت بردن و خوش‌گذرانی بخشی از زندگی همه‌ی ماست. اما وقتی از لذت‌جویی به عنوان یک ارزش صحبت می‌کنیم، منظور این است که میزان لذت و خوشی می‌تواند در انتخاب‌ها و تصمیم‌های فرد نقش مهمی داشته باشد.',
				'هرچه این ارزش جایگاه بالاتری پیدا کند، تجربه‌های لذت‌بخش و خوشایند می‌توانند در انتخاب بین گزینه‌های مختلف وزن بیشتری پیدا کنند.',
				'پیش از پرسشنامه‌ی شوارتز هم روان‌شناسان و فیلسوفان مختلف درباره‌ی لذت به عنوان یکی از انگیزه‌های مهم انسان صحبت کرده‌اند؛ از جمله فروید و اپیکور.'
			]
		},

		Achievement: {
			description: 'میزان اهمیت موفقیت، دستاورد و نشان دادن شایستگی به دیگران برای شما.',
			definition: 'موفقیت شخصی از راه نشان دادن شایستگی بر اساس معیارهای اجتماعی.',
			dimension: 'خودافزایی',
			alt: ['پیشرفت', 'کسب دستاورد'],
			details: [
				'در این ارزش، فقط خودِ موفق شدن مطرح نیست؛ دیده شدن و به رسمیت شناخته شدنِ دستاوردها هم اهمیت دارد.',
				'بنابراین وقتی موفقیت در جایگاه بالاتری از ارزش‌های فرد قرار می‌گیرد، دستاورد، پیشرفت و نشان دادن شایستگی می‌تواند در انتخاب‌های او نقش پررنگ‌تری داشته باشد.',
				'این مفهوم به تعریفی که در بسیاری از نظریه‌های موفقیت از دستاورد و موفقیت شخصی ارائه می‌شود، نزدیک است.'
			]
		},

		Power: {
			description: 'میزان اهمیت ثروت، اقتدار و جایگاه اجتماعی برای شما.',
			definition: 'جایگاه و اعتبار اجتماعی، و کنترل یا تسلط بر مردم و منابع.',
			dimension: 'خودافزایی',
			alt: ['قدرت‌خواهی', 'برتری‌طلبی'],
			details: [
				'قدرت یکی از ارزش‌هایی است که در بسیاری از پژوهش‌ها و نظریه‌های مربوط به انگیزه‌ها، ارزش‌ها و فرهنگ‌های انسانی به آن پرداخته شده است.',
				'در مدل شوارتز، قدرت مفاهیمی مثل ثروت، اقتدار، اعتبار و جایگاه اجتماعی و همچنین کنترل منابع و دیگران را در بر می‌گیرد.',
				'بنابراین این ارزش فقط به معنای «قدرت سیاسی» یا «دستور دادن به دیگران» نیست و دامنه‌ی گسترده‌تری دارد.'
			]
		},

		Security: {
			description: 'میزان اهمیت امنیت، ثبات و آرامش در زندگی، خانواده و جامعه برای شما.',
			definition: 'ایمنی، هماهنگی و پایداری جامعه، روابط و خودِ فرد.',
			dimension: 'حفظ وضع موجود',
			alt: ['ایمنی'],
			details: [
				'امنیت برای بیشتر ما یک نیاز آشناست و می‌تواند جنبه‌های مختلفی از زندگی را در بر بگیرد.',
				'در مدل شوارتز، امنیت فقط به معنای در امان بودن از خطرهای شخصی نیست؛ ثبات محیط، امنیت خانواده و نزدیکان و حتی ثبات جامعه هم در این مفهوم قرار می‌گیرد.',
				'در نتیجه، این ارزش تصویری نسبتاً گسترده از نیاز به امنیت، آرامش و قابل‌پیش‌بینی بودن شرایط زندگی ارائه می‌دهد.'
			]
		},

		Benevolence: {
			description: 'میزان اهمیت کمک، حمایت و حفظ رفاه دوستان، خانواده و افراد نزدیک برای شما.',
			definition: 'حفظ و افزایش رفاه کسانی که فرد با آن‌ها در تماس شخصی و مکرر است.',
			dimension: 'خودفراروی',
			alt: ['نیک‌جویی'],
			details: [
				'در این‌جا منظور از خیرخواهی، بیشتر توجه و کمک به افرادی است که ارتباط شخصی و نزدیکی با آن‌ها داریم؛ مثل خانواده، دوستان و اطرافیان.',
				'بنابراین این ارزش را می‌توان به مفهوم حمایت از افراد نزدیک و اهمیت دادن به رفاه آن‌ها نزدیک دانست.',
				'تفاوتش با جهان‌شمولی این است که دامنه‌ی خیرخواهی در این‌جا بیشتر به حلقه‌ی نزدیکان محدود می‌شود.'
			]
		},

		Universalism: {
			description: 'میزان اهمیت رفاه همه‌ی انسان‌ها، پذیرش تفاوت‌ها و حفظ طبیعت برای شما.',
			definition: 'درک، قدردانی، مدارا و حمایت از رفاه همه‌ی مردم و طبیعت.',
			dimension: 'خودفراروی',
			alt: ['نگرش جهان‌شمول'],
			details: [
				'در کنار خیرخواهی نسبت به نزدیکان، شوارتز یک ارزش جداگانه برای توجه به دیگران و طبیعت در نظر می‌گیرد.',
				'در این ارزش، رفاه انسان‌ها به طور کلی، پذیرش و مدارا با تفاوت‌ها و توجه به طبیعت اهمیت پیدا می‌کند؛ حتی وقتی با افرادی روبه‌رو هستیم که ارتباط مستقیمی با آن‌ها نداریم.',
				'تفاوت مهم این ارزش با خیرخواهی این است که دامنه‌ی توجه در این‌جا از خانواده و دوستان فراتر می‌رود و همه‌ی مردم و طبیعت را در بر می‌گیرد.'
			]
		},

		Tradition: {
			description: 'میزان اهمیت آداب، باورها و اصولی که از فرهنگ، خانواده یا گذشته به شما رسیده است.',
			definition: 'احترام، تعهد و پذیرش آداب و ایده‌هایی که فرهنگ یا دینِ سنتی در اختیار فرد می‌گذارد.',
			dimension: 'حفظ وضع موجود',
			alt: [],
			details: [
				'در مدل شوارتز، سنت به اهمیت دادن به باورها، اصول، آداب و روش‌هایی اشاره دارد که از گذشته و از طریق فرهنگ یا دین به فرد منتقل شده‌اند.',
				'این ارزش فقط به انجام دادن چند رسم خاص محدود نمی‌شود؛ بلکه می‌تواند شامل احترام به میراث فرهنگی و فکری گذشته و پایبندی به آن‌ها هم باشد.',
				'هرچه این ارزش جایگاه بالاتری داشته باشد، احتمال بیشتری دارد که فرد این باورها و سنت‌ها را در انتخاب‌ها و شیوه‌ی زندگی خود در نظر بگیرد.'
			]
		},

		Conformity: {
			description: 'میزان اهمیت هماهنگ بودن با دیگران و رعایت هنجارها و انتظارات اجتماعی برای شما.',
			definition: 'خویشتن‌داری در کارها و تمایلاتی که ممکن است دیگران را آزار دهد یا انتظارات و هنجارهای اجتماعی را نقض کند.',
			dimension: 'حفظ وضع موجود',
			alt: ['همسازی', 'همرنگی با جمع'],
			details: [
				'همنوایی یا همسازی به این معناست که فرد تلاش می‌کند از ایجاد اصطکاک و تعارض غیرضروری با اطرافیان و جامعه جلوگیری کند.',
				'این ارزش می‌تواند خودش را در رعایت قوانین و هنجارها، توجه به انتظارات دیگران و کنترل رفتارهایی که ممکن است باعث آزار دیگران شوند نشان دهد.',
				'هرچه این ارزش جایگاه بالاتری داشته باشد، هماهنگی با دیگران و پرهیز از تعارض ممکن است در انتخاب‌ها و رفتارهای فرد نقش بیشتری پیدا کند.'
			]
		},

		Stimulation: {
			description: 'میزان اهمیت تنوع، هیجان، تازگی و تجربه‌های جدید برای شما.',
			definition: 'هیجان، تازگی و چالش در زندگی.',
			dimension: 'گشودگی به تغییر',
			alt: ['برانگیختگی', 'جستجوی برانگیختگی', 'هیجان‌خواهی'],
			details: [
				'این ارزش به علاقه به تجربه‌های تازه، هیجان، تنوع و چالش در زندگی مربوط می‌شود.',
				'برای کسی که این ارزش جایگاه بالاتری دارد، تغییر و تجربه‌های جدید لزوماً تهدیدکننده نیستند و می‌توانند بخشی جذاب از زندگی باشند.',
				'ریسک کردن، امتحان کردن چیزهای جدید و قرار گرفتن در موقعیت‌های متفاوت می‌تواند از جلوه‌های این ارزش باشد.'
			]
		},

		'Self-direction': {
			description: 'میزان اهمیت استقلال فکری و عملی، انتخاب آزادانه و دنبال کردن مسیر خودتان برای شما.',
			definition: 'تفکر و عمل مستقل: انتخاب کردن، آفریدن و کاوش کردن.',
			dimension: 'گشودگی به تغییر',
			alt: ['خودرهبری', 'خودرهنمودی', 'خودجهت‌دهی'],
			details: [
				'مفهوم اصلی در خودرهبری، استقلال است؛ یعنی فرد ترجیح می‌دهد خودش فکر کند، انتخاب کند و درباره‌ی مسیر زندگی‌اش تصمیم بگیرد.',
				'این ارزش فقط به مستقل بودن در تصمیم‌گیری محدود نمی‌شود و خلاقیت، کنجکاوی و کشف مسیرهای جدید را هم در بر می‌گیرد.',
				'در توصیف شوارتز، مفاهیمی مثل استقلال، خلاقیت، آزادی در انتخاب اهداف و کنجکاوی در کنار هم قرار می‌گیرند.'
			]
		}
	};

	let totalQuestions = QUESTIONS.length;
	let answers = $state<number[]>(Array(totalQuestions).fill(0));
	let step = $state(0);
	let showResult = $state(false);
	let result = $state([
		{
			label: "لذت‌جویی | Hedonism",
			questions: [10, 26, 37],
			score: 0
		},
		{
			label: "موفقیت | Achievement",
			questions: [4, 13, 24, 32],
			score: 0
		},
		{
			label: "کسب قدرت | Power",
			questions: [2, 17, 39],
			score: 0
		},
		{
			label: "امنیت | Security",
			questions: [5, 14, 21, 31, 35],
			score: 0
		},
		{
			label: "خیرخواهی | Benevolence",
			questions: [12, 18, 27, 33],
			score: 0
		},
		{
			label: "جهان‌نگری | Universalism",
			questions: [3, 8, 19, 23, 29, 40],
			score: 0
		},
		{
			label: "سنت | Tradition",
			questions: [9, 20, 25, 38],
			score: 0
		},
		{
			label: "همنوایی | Conformity",
			questions: [7, 16, 28, 36],
			score: 0
		},
		{
			label: "تحریک‌طلبی | Stimulation",
			questions: [6, 15, 30],
			score: 0
		},
		{
			label: "خوداتکایی | Self-direction",
			questions: [1, 11, 22, 34],
			score: 0
		}
	])

	// نتایج مرتب‌شده بر اساس امتیاز (نزولی)؛ در امتیاز برابر، ترتیب اصلی حفظ می‌شود
	let sortedResult = $derived([...result].sort((a, b) => b.score - a.score));

	function nextBtn() {
		if (step < totalQuestions) {
			step++;
		} else {
			result.forEach((topic) => {
				let score = 0
				topic.questions.forEach(questionNumber => {
					score += answers[questionNumber - 1]
				})
				topic.score = Math.round(score * 10 / topic.questions.length) / 10
			});
			showResult = true;
		}
	}
</script>

<svelte:head>
	<title>پرسشنامه ارزش‌های شخصی</title>

	<link
		rel="stylesheet"
		href="https://cdn.jsdelivr.net/gh/rastikerdar/vazirmatn@v33.003/Vazirmatn-font-face.css"
	/>
</svelte:head>

<div dir="rtl" class="app min-h-screen">

	<!-- Header -->
	<header class="border-b border-gray-200/80 bg-white/80 backdrop-blur-md">
		<div class="mx-auto flex max-w-4xl items-center justify-between px-5 py-4">

			<div>
				<h1 class="text-base font-bold text-gray-800 sm:text-lg">
					پرسشنامه ارزش‌های شخصی
				</h1>

				<p class="mt-0.5 text-xs text-gray-500">
					ارزش‌های فردی شوارتز
				</p>
			</div>

			<div
				hidden={step === 0 || showResult == true}
				class="rounded-full bg-gray-100 px-3 py-1.5 text-xs font-semibold text-gray-600"
			>
				{step} از {totalQuestions}
			</div>

		</div>
	</header>


	<!-- Main -->
	<main
		class="mx-auto flex min-h-[calc(100vh-81px)] w-full max-w-4xl items-center justify-center px-4 py-6 sm:px-6"
	>

		<div class="w-full max-w-2xl">

			<!-- Question Card -->
			<div
				class="overflow-hidden rounded-2xl border border-gray-200 bg-white shadow-lg shadow-gray-200/50"
			>

				<div class="p-5 sm:p-7">

					{#if showResult}
						<div class="mb-6">

							<!-- Result Header -->
							<div class="mb-6 text-center">
								<h2 class="text-2xl font-bold text-gray-800">
									نتیجه پرسشنامه
								</h2>

								<p class="mt-2 text-sm leading-6 text-gray-500">
									امتیاز شما در هر یک از ارزش‌های فردی شوارتز
								</p>
							</div>


							<!-- Results -->
							<div class="grid items-start gap-3 sm:grid-cols-2">

								{#each sortedResult as topic (topic.label)}

									{@const percentage = Math.round((topic.score / 6) * 100)}
									{@const info = TOPIC_INFO[topic.label.split(' | ')[1]]}

									<div
										class="rounded-2xl border border-gray-100 bg-gray-50/70 p-4 transition hover:border-primary-100 hover:bg-primary-50/30"
									>

										<div class="flex items-center gap-4">

										<!-- Circular Progress -->
										<div
											class="relative flex h-16 w-16 shrink-0 items-center justify-center rounded-full"
											style={`background: conic-gradient(#6366f1 ${percentage}%, #e5e7eb 0)`}
										>

											<div
												class="flex h-12 w-12 items-center justify-center rounded-full bg-white"
											>
												<span class="text-sm font-bold text-gray-700">
													{topic.score}
												</span>
											</div>

										</div>


										<!-- Topic -->
										<div class="min-w-0 flex-1">

											<p class="text-sm font-semibold leading-6 text-gray-800">
												{topic.label.split(' | ')[0]}
											</p>

											<p class="mt-0.5 text-xs text-gray-400">
												{topic.label.split(' | ')[1]}
											</p>

											<!-- Small progress bar -->
											<div class="mt-2 h-1.5 overflow-hidden rounded-full bg-gray-200">
												<div
													class="h-full rounded-full bg-primary-500 transition-all duration-700"
													style={`width: ${percentage}%`}
												></div>
											</div>

										</div>

									</div>

										<!-- Description -->
										<p class="mt-3 text-xs leading-6 text-gray-600">
											{info.description}
										</p>

										<!-- Read more -->
										<details class="mt-2">
											<summary
												class="cursor-pointer select-none text-xs font-semibold text-primary-600 hover:text-primary-700"
											>
												بیشتر بخوانید
											</summary>

											<div
												class="mt-3 space-y-3 border-t border-gray-200 pt-3 text-xs leading-6 text-gray-600"
											>
												<p>
													<span class="font-semibold text-gray-700">تعریف شوارتز: </span>{info.definition}
												</p>

												{#each info.details as paragraph}
													<p>{paragraph}</p>
												{/each}

												<p class="text-gray-400">
													دسته‌ی کلان: {info.dimension}
												</p>

												{#if info.alt.length}
													<p class="text-gray-400">
														ترجمه‌های دیگر: {info.alt.join('، ')}
													</p>
												{/if}
											</div>
										</details>
									</div>

								{/each}

							</div>


							<!-- Scale -->
							<div
								class="mt-5 rounded-xl border border-gray-100 bg-gray-50 p-4 text-center"
							>
								<p class="text-xs leading-6 text-gray-500">
									امتیاز هر ارزش بین <strong>۱</strong> تا <strong>۶</strong> است.
									امتیاز بالاتر نشان‌دهنده اهمیت بیشتر آن ارزش برای شماست.
								</p>
							</div>

						</div>


						<!-- Result Navigation -->
						<div class="mt-6 flex justify-center border-t border-gray-100 pt-5">

							<Button
								color="light"
								onclick={() => {
									showResult = false;
									step = 0;
									answers = Array(totalQuestions).fill(0);
								}}
								class="!rounded-xl !px-5"
							>
								شروع دوباره
							</Button>

						</div>
					{:else if step > 0}
					<!-- Question heading -->
					<div class="mb-5">
						<div
							class="mb-3 inline-flex items-center rounded-full bg-primary-50 px-3 py-1 text-xs font-semibold text-primary-700"
						>
							پرسش {step}
						</div>

						<h2
							class="text-lg font-bold leading-8 text-gray-800 sm:text-xl sm:leading-9"
						>
							{QUESTIONS[step - 1]}
						</h2>

						<p class="mt-2 text-xs text-gray-400 sm:text-sm">
							چقدر شبیه چنین فردی هستی؟
						</p>

					</div>


					<!-- Answers -->
					<div class="space-y-2">

						{#each options as option}
							<label
								class:selected={answers[step - 1] === option.value}
								class="answer-option flex cursor-pointer items-center gap-3 rounded-xl border px-4 py-3 transition-all duration-150"
							>
								<Radio
									name="pvq-answer"
									value={option.value}
									bind:group={answers[step - 1]}
								/>

								<span class="text-sm font-medium text-gray-700">
									{option.label}
								</span>
							</label>
						{/each}

					</div>


					<!-- Navigation -->
					<div
						class="mt-6 flex items-center justify-between border-t border-gray-100 pt-5"
					>

						<Button
							color="light"
							disabled={step === 1}
							onclick={() => step--}
							class="!rounded-xl"
						>
							قبلی
						</Button>


						<Button
							color="light"
							onclick={nextBtn}
							class="!rounded-xl !px-5"
						>
							{step === totalQuestions ? 'مشاهده نتیجه' : 'بعدی'}
						</Button>

					</div>
				{:else}
					<div class="mb-6">

						<!-- Title -->
						<div class="mb-4 flex items-center gap-3">
							<div class="h-8 w-1 rounded-full bg-primary-600"></div>

							<div>
								<h2 class="mt-1 text-xl font-bold leading-8 text-gray-800 sm:text-2xl">
									چطور این توصیف‌ها به شما شباهت دارند؟
								</h2>
							</div>
						</div>


						<!-- Introduction -->
						<p class="text-sm leading-7 text-gray-600 sm:text-base sm:leading-8">
							در این پرسشنامه، ۴۰ جمله درباره یک فرد فرضی ارائه می‌شود.
							فرض کنید این فرد را نمی‌شناسید و شخص دیگری در حال معرفی او به شماست.
							پس از خواندن هر توصیف، گزینه‌ای را انتخاب کنید که نشان می‌دهد
							این فرد تا چه اندازه به شما شباهت دارد.
						</p>


						<!-- Scale -->
						<div class="mt-5 rounded-xl border border-gray-100 bg-gray-50/70 p-4">

							<p class="mb-3 text-xs font-semibold text-gray-500">
								مقیاس پاسخ‌ها
							</p>

							<div class="grid grid-cols-1 gap-2 sm:grid-cols-2 lg:grid-cols-3">

								<div class="flex items-center gap-2 text-sm text-gray-600">
									<span class="flex h-6 w-6 shrink-0 items-center justify-center rounded-md bg-white text-xs font-bold text-gray-500 shadow-sm">
										۱
									</span>
									<span>اصلاً شبیه من نیست</span>
								</div>

								<div class="flex items-center gap-2 text-sm text-gray-600">
									<span class="flex h-6 w-6 shrink-0 items-center justify-center rounded-md bg-white text-xs font-bold text-gray-500 shadow-sm">
										۲
									</span>
									<span>شبیه من نیست</span>
								</div>

								<div class="flex items-center gap-2 text-sm text-gray-600">
									<span class="flex h-6 w-6 shrink-0 items-center justify-center rounded-md bg-white text-xs font-bold text-gray-500 shadow-sm">
										۳
									</span>
									<span>خیلی کم شبیه من است</span>
								</div>

								<div class="flex items-center gap-2 text-sm text-gray-600">
									<span class="flex h-6 w-6 shrink-0 items-center justify-center rounded-md bg-white text-xs font-bold text-gray-500 shadow-sm">
										۴
									</span>
									<span>تا حدی شبیه من است</span>
								</div>

								<div class="flex items-center gap-2 text-sm text-gray-600">
									<span class="flex h-6 w-6 shrink-0 items-center justify-center rounded-md bg-white text-xs font-bold text-gray-500 shadow-sm">
										۵
									</span>
									<span>شبیه من است</span>
								</div>

								<div class="flex items-center gap-2 text-sm text-gray-600">
									<span class="flex h-6 w-6 shrink-0 items-center justify-center rounded-md bg-white text-xs font-bold text-gray-500 shadow-sm">
										۶
									</span>
									<span>خیلی شبیه من است</span>
								</div>

							</div>
						</div>


						<!-- Schwartz note -->
						<p class="mt-4 text-xs leading-6 text-gray-400">
							شوارتز تعداد ارزش‌ها را محدود به ده مورد نمی‌داند؛
							اما مطالعات او نشان داده‌اند که بیشتر ارزش‌های انسانی را می‌توان
							در یکی از این ده دسته جای داد.
						</p>

					</div>


					<!-- Navigation -->
					<div
						class="mt-6 flex items-center justify-center border-t border-gray-100 pt-5"
					>

						<Button
							color="light"
							onclick={()=> step++}
							class="!rounded-xl !px-5"
						>
							شروع
						</Button>

					</div>
				{/if}
				</div>

			</div>


			<!-- Footer -->
			<div class="mt-4 flex items-center justify-center gap-3 text-[11px] text-gray-400">
				<span>حاصل اوقات فراغت</span>
				<a
					href="https://www.linkedin.com/in/aliroustaei"
					target="_blank"
					rel="noopener noreferrer"
					class="transition-colors hover:text-gray-600"
				>
					آمیرزا
				</a>

				<span class="text-gray-300">•</span>

				<a
					href="https://github.com/ali-roustaei/pvq"
					target="_blank"
					rel="noopener noreferrer"
					class="transition-colors hover:text-gray-600"
				>
					GitHub
				</a>
			</div>

		</div>

	</main>

</div>


<style>
	:global(body) {
		margin: 0;
		font-family: 'Vazirmatn', sans-serif;
	}

	:global(*) {
		font-family: 'Vazirmatn', sans-serif;
	}

	.app {
		background:
			radial-gradient(
				circle at 50% 0%,
				rgba(99, 102, 241, 0.06),
				transparent 40%
			),
			#f8fafc;
	}

	.answer-option {
		border-color: #e5e7eb;
		background: #ffffff;
	}

	.answer-option:hover {
		border-color: #c7d2fe;
		background: #f8faff;
		transform: translateY(-1px);
	}

	.answer-option.selected {
		border-color: #818cf8;
		background: #eef2ff;
		box-shadow: 0 0 0 1px rgba(99, 102, 241, 0.15);
	}

	.answer-option.selected span {
		color: #4338ca;
	}

	@media (max-width: 640px) {
		.app {
			background: #f8fafc;
		}

		.answer-option {
			padding-top: 0.7rem;
			padding-bottom: 0.7rem;
		}
	}
</style>