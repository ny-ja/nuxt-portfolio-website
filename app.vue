<script setup>
import { ref, onMounted, provide } from 'vue';
import FreelanceLogo from '~/assets/images/freelance-logo.jpg';
import S4Logo from '~/assets/images/s4-logo.png';
import AclcLogo from '~/assets/images/aclc-logo.png';
import CmuLogo from '~/assets/images/cmu-logo.jpg';
import DictDiagnosticCertificate from '~/assets/certificates/dict-diagnostic-certificate.jpeg';
import HackathonCertificate from '~/assets/certificates/hackathon-certificate.png';
import JavaBootcampCertificate from '~/assets/certificates/java-bootcamp-certificate.png';
import PhpCertificate from '~/assets/certificates/php-certificate.jpg';

onMounted(() => {
  setTimeout(() => {
    isLoading.value = false;
  }, 5000);
});

const isLoading = ref(true);

const scrollToSection = (sectionId) => {
  const section = document.getElementById(sectionId)
  if (section) {
    section.scrollIntoView({ behavior: 'smooth' })
  }
}

provide('scrollToSection', scrollToSection)
</script>

<template>
  <div>
    <Loader v-if="isLoading" />
    <div v-else class="bg-gray-100 text-black dark:bg-black dark:text-white min-h-[100vh]">
      <div class="md:px-[calc(50%-20rem)] px-6">
        <section id="home" class="pt-6 md:pt-12 lg:pt-18">
          <div class="flex space-x-6 justify-between items-center">
            <div class="flex flex-col">
              <h1 class="lg:text-[60px] md:text-[50px] text-[25px] font-bold tracking-tighter">
                Hi, I'm Johnny👋
              </h1>
              <span class="tracking-tighter font-medium lg:text-[20px] md:text-[18px] text-md">Full Stack Web Developer
                and Freelancer, passionate about
                building impactful web solutions and helping others succeed.</span>
            </div>
            <img class="lg:size-28 md:size-24 size-20 rounded-full" src="~/assets/images/profile-photo.png"
              alt="Profile Photo">
          </div>
          <DownloadCV class="mt-6">
            <template #text>Download CV</template>
          </DownloadCV>
        </section>

        <section id="about">
          <div class="mt-12">
            <h1 class="font-bold text-2xl">About</h1>
          </div>
          <p class="font-medium">I'm a Full Stack Web Developer with strong experience
            in <span @click.prevent="scrollToSection('skills')"
              class="text-teal-500 hover:text-teal-700 underline cursor-pointer">Laravel,
              Inertia.js, and Vue.js,</span> focused on building dynamic,
            user-friendly, and scalable web apps. <span @click.prevent="scrollToSection('projects')"
              class="text-teal-500 hover:text-teal-700 underline cursor-pointer">I excel in both front-end
              and back-end development, solving complex problems,
              optimizing performance, and delivering elegant designs.</span>
          </p>
        </section>

        <section id="experiences">
          <div class="mt-12 mb-2">
            <h1 class="font-bold text-2xl">Work Experiences</h1>
          </div>
          <div class="space-y-4">
            <ExperienceCard title="Freelance Full Stack Developer" duration="Jan 2022 - Present" :responsibilities="[
              'Developed custom academic projects and capstone solutions, specializing in full-stack development.',
              'Collaborated with students to transform project ideas into functional applications.',
              'Delivered projects on tight deadlines, focusing on clean code and maintainable solutions.',
            ]"
              :tags="['Java', 'Laravel', 'Arduino', 'Firebase', 'MySQL', 'React.js', 'Vue.js', 'Tailwind CSS', 'API Integration']"
              :logo="FreelanceLogo" />

            <ExperienceCard title="Full Stack Web Developer" companyName="Split Second Software Services Corporation"
              companyLink="https://splitsecondsoftware.com/" duration="March 2024 - July 2024" :responsibilities="[
                'Developed dynamic, feature-rich web applications using Laravel for backend operations and Vue.js for front-end interfaces, ensuring seamless user experiences.',
                'Built reusable Vue components and implemented efficient state management with Vuex, following best practices for maintainable and modular code.',
                'Integrated Laravel Inertia.js to create SPA-like (Single Page Application) functionality without compromising on SEO and performance.',
                'Enhanced UI elements and interactivity using Vue transitions, Tailwind CSS, and third-party libraries to provide a polished user interface.',
                'Leveraged Laravel Livewire for real-time interactivity, improving data handling in complex forms and dynamic components.'
              ]" :tags="['Laravel', 'Vue.js', 'Tailwind CSS', 'API Integration']" :logo="S4Logo" />
          </div>
        </section>

        <section id="educations">
          <div class="mt-12 mb-2">
            <h1 class="font-bold text-2xl">Education</h1>
          </div>
          <div class="space-y-4">
            <EducationCard degree="Bachelor of Science in Information Technology"
              schoolName="AMA Computer Learning Center College of Bukidnon" schoolLink="https://aclcbukidnon.com/"
              duration="2022 - 2024" :logo="AclcLogo" />
            <EducationCard degree="Bachelor of Science in Information Technology"
              schoolName="Central Mindanao University" schoolLink="https://www.cmu.edu.ph/" duration="2018 - 2022"
              :logo="CmuLogo" />
          </div>
        </section>

        <section id="skills">
          <div class="mt-12 mb-2">
            <h1 class="font-bold text-2xl">Skills</h1>
          </div>
          <div class="flex flex-wrap gap-y-2 gap-x-2">
            <Tag text="Java" size="md" />
            <Tag text="Vue.js" size="md" />
            <Tag text="Laravel" size="md" />
            <Tag text="Inertia.js" size="md" />
            <Tag text="Javascript" size="md" />
            <Tag text="Tailwind CSS" size="md" />
            <Tag text="MySQL" size="md" />
            <Tag text="Kotlin" size="md" />
            <Tag text="PHP" size="md" />
            <Tag text="Node.js" size="md" />
            <Tag text="Nuxt.js" size="md" />
            <Tag text="HTML" size="md" />
            <Tag text="CSS" size="md" />
          </div>
        </section>

        <section id="projects">
          <div class="my-12">
            <SectionTitle>
              <template #icon>
                <ProjectIcon />
              </template>
              <template #title>Projects</template>
            </SectionTitle>
            <SectionSubtitle>
              <template #subtitle>Showcasing My Journey in Crafting Web Experiences</template>
            </SectionSubtitle>
          </div>
          <Projects />
        </section>

        <section id="certifications">
          <div class="my-12">
            <SectionTitle>
              <template #icon>
                <CertificateIcon />
              </template>
              <template #title>Certifications</template>
            </SectionTitle>
            <SectionSubtitle>
              <template #subtitle>Highlighting My Achievements and Expertise</template>
            </SectionSubtitle>
          </div>
          <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-2 gap-6">
            <CertificationCard awardTitle="DICT Diagnostic Examination" date="May 14, 2024"
              :backgroundImage="DictDiagnosticCertificate"
              issuingOrganization="Department of Information and Communication Technology" />
            <CertificationCard awardTitle="PHP Course Certificate" date="June 20, 2023"
              :backgroundImage="PhpCertificate" issuingOrganization="Sololearn" />
            <CertificationCard awardTitle="InnoVa Hackathon Certificate of Participation" date="June 26, 2024"
              :backgroundImage="HackathonCertificate" issuingOrganization="ICT Counsel of Valencia City" />
            <CertificationCard awardTitle="Java Programming Bootcamp Certificate of Completion"
              date="November 20-24, 2023" :backgroundImage="JavaBootcampCertificate"
              issuingOrganization="Department of Information and Communication Technology" />
          </div>
        </section>

        <section id="contact" class="pb-32">
          <div class="my-12">
            <SectionTitle>
              <template #icon>
                <ContactIcon />
              </template>
              <template #title>Contact</template>
            </SectionTitle>
            <SectionSubtitle>
              <template #subtitle>Let’s Connect and Collaborate</template>
            </SectionSubtitle>
          </div>
          <p class="text-center text-xl text-gray-500">Want to chat? Just shoot me a dm <a href="https://m.me/nyjaaaaa"
              target="_blank" class="text-blue-500">with
              a direct
              question on
              messenger</a> and
            I'll respond whenever I can.</p>
        </section>
      </div>

      <div class="fixed z-40 max-w-lg -translate-x-1/2 bottom-6 left-1/2">
        <NavSection />
      </div>

    </div>
  </div>
</template>
