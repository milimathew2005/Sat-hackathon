# Sat-hackathon
![Novel Frame](https://github.com/TH-Activities/saturday-hack-night-template/assets/90635335/4c26e8ac-2dd1-4d75-8e1a-9f7585e3b381)
#Essay Generator
It is an  algorithm that draws knowledge from available data to understand what the message is and  wraps sentences and words around it, i.e. creates the summary or essay, would tremendously help the writer in expressing his message as concise as possible. In this context, we designed a text generation tool using Google Assistant to easily generate essays based on message-relevant input variables such as key words and intention indicators.
console.log("Welcome to Unniyappam.ai !!");
class MarkovChain {
  constructor() {
    this.chain = {};
    this.startWords = [];
  }

  addText(text) {
    const words = text.split(' ');

    if (words.length < 2) {
      return;
    }

    this.startWords.push(words[0]);

    for (let i = 0; i < words.length - 1; i++) {
      const currentWord = words[i];
      const nextWord = words[i + 1];

      if (!this.chain[currentWord]) {
        this.chain[currentWord] = [];
      }

      this.chain[currentWord].push(nextWord);
    }
  }

  generateText(maxLength = 100) {
    const startWord = this.startWords[Math.floor(Math.random() * this.startWords.length)];
    let currentWord = startWord;
    let generatedText = [currentWord];

    while (generatedText.length < maxLength) {
      if (!this.chain[currentWord]) {
        break;
      }

      const nextWords = this.chain[currentWord];
      const nextWord = nextWords[Math.floor(Math.random() * nextWords.length)];

      generatedText.push(nextWord);
      currentWord = nextWord;
    }

    return generatedText.join(' ');
  }
}

// Example usage
const essayGenerator = new MarkovChain();

const sampleText = `
  Technology has become an integral part of modern society. It has revolutionized the way we communicate, work, and live. 
  The impact of technology on society is profound, influencing everything from education to healthcare.
  In the 21st century, it is undeniable that technology has seamlessly integrated itself into every facet of modern society. From the moment we wake up to the alarm on our smartphones to the automated systems that govern our cities, technology has transformed the way we live, work, communicate, and even think. It has become an integral force, shaping the very essence of our existence.

Body:

Communication Revolution:

Technology has revolutionized the way we communicate. Gone are the days when sending a letter meant waiting for days or even weeks for a response. With the advent of the internet and smartphones, we can now connect with anyone, anywhere, in an instant. Social media platforms have bridged geographical gaps, allowing us to stay in touch with friends and family globally. Video conferencing has transformed the business landscape, making remote work and collaboration a reality.

Information Access:

The digital age has democratized information access. The internet has made a vast sea of knowledge available to anyone with a connection. Online courses, e-books, and educational websites have revolutionized learning. Today, students can access lectures from prestigious universities worldwide, transcending borders and socioeconomic barriers.

Economic Transformation:

Technology has reshaped economies. E-commerce has become the norm, with online shopping and digital payment systems simplifying transactions. Automation and artificial intelligence have increased productivity in industries, while the gig economy and freelance work have expanded opportunities for employment.

Healthcare Advancements:

Modern healthcare heavily relies on technology. Diagnostic tools, telemedicine, and electronic health records have improved patient care and accessibility. Research is accelerated through powerful computing, leading to breakthroughs in treatments and therapies.

Environmental Sustainability:

Technology plays a pivotal role in addressing environmental challenges. Renewable energy sources, smart grids, and energy-efficient technologies are reducing carbon footprints. Innovations in transportation, like electric vehicles, are contributing to a greener future.

Cultural Impact:

Technology has also shaped our culture. The entertainment industry, including music, movies, and gaming, has been revolutionized by digital media and streaming platforms. Social issues and political movements find global support and momentum through online platforms, amplifying voices that were once marginalized.


 Technology's pervasive influence is undeniable. It has evolved from being a convenience to an indispensable aspect of our lives. While its impact has been overwhelmingly positive, we must also navigate the challenges it presents, such as digital privacy and the potential for job displacement. Nevertheless, technology continues to drive progress, innovation, and interconnectedness, making it an integral force in shaping the modern world. As we move forward, our ability to harness technology's potential for the greater good will determine the course of our future.
`;

essayGenerator.addText(sampleText);

const generatedEssay = essayGenerator.generateText();
console.log(generatedEssay);
