<template>
    <footer class="bg-gray-900" aria-labelledby="footer-heading">
        <h2 id="footer-heading" class="sr-only">Footer</h2>
        <div class="mx-auto max-w-7xl px-6 py-16 sm:py-24 lg:px-8 lg:py-32">
            <div class="xl:grid xl:grid-cols-3 xl:gap-8">
                <div style="margin-left: 160px">
                    <img class="h-7" src="https://500apps.com/images/500_apps_logo_footer.png?v=1680701393359498964" alt="Company name" />
                    <p class="text-sm leading-6 text-gray-300 hover:text-white mt-6">Get access to 50 Fortune 500 standard apps to help you take your growing business to the next level.</p>
                    <p class="text-sm leading-6 text-gray-300 hover:text-white mt-6">99 Wall Street #1135 New York, NY 10005</p>
                </div>
                <div class="mt-16 grid grid-cols-2 gap-8 xl:col-span-2 xl:mt-0">
                    <div class="md:grid md:grid-cols-2 md:gap-8">
                        <div>
                            <h3 class="text-sm font-semibold leading-6 text-white">Productivity</h3>
                            <ul role="list" class="mt-6 space-y-4">
                                <li v-for="item in navigation.solutions" :key="item.name">
                                    <a :href="item.href" class="text-sm leading-6 text-gray-300 hover:text-white">{{ item.name }}</a>
                                </li>
                            </ul>
                        </div>
                        <div class="mt-10 md:mt-0">
                            <h3 class="text-sm font-semibold leading-6 text-white">Marketing</h3>
                            <ul role="list" class="mt-6 space-y-4">
                                <li v-for="item in navigation.support" :key="item.name">
                                    <a :href="item.href" class="text-sm leading-6 text-gray-300 hover:text-white">{{ item.name }}</a>
                                </li>
                            </ul>
                        </div>
                    </div>
                    <div class="md:grid md:grid-cols-2 md:gap-8">
                        <div>
                            <h3 class="text-sm font-semibold leading-6 text-white">Collaboration</h3>
                            <ul role="list" class="mt-6 space-y-4">
                                <li v-for="item in navigation.company" :key="item.name">
                                    <a :href="item.href" class="text-sm leading-6 text-gray-300 hover:text-white">{{ item.name }}</a>
                                </li>
                            </ul>
                        </div>
                        <div class="mt-10 md:mt-0">
                            <h3 class="text-sm font-semibold leading-6 text-white">Sales</h3>
                            <ul role="list" class="mt-6 space-y-4">
                                <li v-for="item in navigation.legal" :key="item.name">
                                    <a :href="item.href" class="text-sm leading-6 text-gray-300 hover:text-white">{{ item.name }}</a>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </footer>
</template>


<script setup lang="ts">
const navigation = {
    response: [
        { name: 'Projectsly', href: '#' },
        { name: 'Forms.io', href: '#' },
        { name: 'Schedule.cc', href: '#' },
        { name: 'BotPath', href: '#' },
        { name: 'BPMApp', href: '#' },
        { name: 'ZapUp', href: '#' },
        { name: 'Sign.cc', href: '#' },
        { name: 'HR & Ops', href: '#' },
        { name: 'Clockly', href: '#' },
        { name: 'RecruitHire', href: '#' },
        { name: 'NinjaInterview', href: '#' },
        { name: 'HRSprout', href: '#' },
        { name: 'PerformanceUp', href: '#' },
        { name: 'LMSNinja', href: '#' },
    ],
    solutions: [
        { name: 'Projectsly', href: '#' },
        { name: 'Forms.io', href: '#' },
        { name: 'Schedule.cc', href: '#' },
        { name: 'BotPath', href: '#' },
        { name: 'BPMApp', href: '#' },
        { name: 'ZapUp', href: '#' },
        { name: 'Sign.cc', href: '#' },
        { name: 'HR & Ops', href: '#' },
        { name: 'Clockly', href: '#' },
        { name: 'RecruitHire', href: '#' },
        { name: 'NinjaInterview', href: '#' },
        { name: 'HRSprout', href: '#' },
        { name: 'PerformanceUp', href: '#' },
        { name: 'LMSNinja', href: '#' },
    ],
    support: [
        { name: 'NinjaSites', href: '#' },
        { name: 'MailSend', href: '#' },
        { name: 'HipSocial', href: '#' },
        { name: 'NinjaSEO', href: '#' },
        { name: 'SiteRecording', href: '#' },
        { name: 'ConvertPath', href: '#' },
        { name: 'NinjaContent', href: '#' },
        { name: 'PushNinja', href: '#' },
        { name: 'Personalize.cc', href: '#' },
        { name: 'NinjaSEM', href: '#' },
    ],
    company: [
        { name: 'Teams.cc', href: '#' },
        { name: 'PBXPlus', href: '#' },
        { name: '500Conference', href: '#' },
        { name: '500Mail', href: '#' },
        { name: '500Box', href: '#' },
        { name: 'Support', href: '#' },
        { name: 'BotUp', href: '#' },
        { name: 'Support.cc', href: '#' },
        { name: 'NinjaChat', href: '#' },
        { name: 'FeedbackUp', href: '#' },
        { name: 'NinjaOnboarding', href: '#' },
        { name: 'UserTracker', href: '#' },
        { name: 'Extensions', href: '#' },
        { name: 'OpenedOrNot', href: '#' },
        { name: 'NinjaCapture', href: '#' },
    ],
    legal: [
        { name: 'Finder.io', href: '#' },
        { name: 'CRM.io', href: '#' },
        { name: 'OutReachly', href: '#' },
        { name: 'OutreachWriter', href: '#' },
        { name: 'Leadsly', href: '#' },
        { name: 'VoxDesk', href: '#' },
        { name: 'Developers', href: '#' },
        { name: 'NinjaAuth', href: '#' },
        { name: 'Unified.cc', href: '#' },
    ],
}
</script>