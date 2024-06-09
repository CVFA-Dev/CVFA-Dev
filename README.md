```javascript
class Myself {
  constructor(info) {
    this.info = info;
  }

  introduction() {
    const currentDate = new Date();
    const birthDate = new Date(this.info.birthYear, this.info.birthMonth - 1, this.info.birthDay);
    const age = currentDate.getFullYear() - birthDate.getFullYear() - (currentDate.getMonth() < birthDate.getMonth() || (currentDate.getMonth() === birthDate.getMonth() && currentDate.getDate() < birthDate.getDate()) ? 1 : 0);
    const yearsOfExperienceAsDeveloper = currentDate.getFullYear() - 2017;

    const introLines = [
      `Hello, I'm ${this.info.nickname}.`,
      `I'm ${age} years old.`,
      `I'm ${this.info.nacionality}.`,
      `I'm a ${this.info.occupation} with ${yearsOfExperienceAsDeveloper} years of experience in ${this.info.devLanguages}.`,
      `GitHub profile: <a href="${this.info.github}" target="_blank">${this.info.github}</a>`,
      `GitLab profile: <a href="${this.info.gitlab}" target="_blank">${this.info.gitlab}</a>`,
      `My YouTube channel: <a href="${this.info.youtube}" target="_blank">${this.info.youtube}</a>`,
      `My Instagram profile: <a href="${this.info.instagram}" target="_blank">${this.info.instagram}</a>`,
      `My Mastodon profile: <a href="${this.info.mastodon}" target="_blank">${this.info.mastodon}</a>`,
      `My website: <a href="${this.info.website}" target="_blank">${this.info.website}</a>`
    ];

    const style = document.createElement('style');
    style.innerHTML = `
      body {
        font-family: Arial, sans-serif;
        background-color: #f0f0f0;
        padding: 20px;
      }

      #intro {
        background-color: #fff;
        border-radius: 5px;
        padding: 20px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        max-width: 500px;
        margin: 0 auto;
      }

      #intro p {
        margin: 0 0 10px;
      }

      #intro a {
        color: #007bff;
        text-decoration: none;
      }

      #intro a:hover {
        text-decoration: underline;
      }
    `;

    document.head.appendChild(style);

    const introDiv = document.createElement('div');
    introDiv.id = 'intro';
    document.body.appendChild(introDiv);

    let lineIndex = 0;
    const interval = setInterval(() => {
      if (lineIndex < introLines.length) {
        introDiv.innerHTML += `<p>${introLines[lineIndex]}</p>`;
        lineIndex++;
      } else {
        clearInterval(interval);
      }
    }, 1000);
  }
}

// Define my informations
const MyInfo = {
  nickname: "Cavifeal",
  nacionality: "Brazilian",
  birthYear: 2008,
  birthMonth: 12,
  birthDay: 31,
  occupation: "Developer",
  devLanguages: "JavaScript and Node.js",
  github: "https://github.com/CVFA-Dev",
  gitlab: "https://gitlab.com/CVFA",
  mastodon: "https://mastodon.social/@CVFA",
  instagram: "https://instagram.com/cvfa_dev",
  youtube: "https://youtube.com/@Cavifeal",
  website: "https://cvfa.vercel.app/"
};

// Create a Myself object
const me = new Myself(MyInfo);

// Introduce myself
me.introduction();
```
