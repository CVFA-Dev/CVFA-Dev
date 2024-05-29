```javascript
    class Myself {
      constructor(info) {
        this.info = info;
      }

      introduction() {
        const currentDate = new Date();
        const birthDate = new Date(this.info.birthYear, this.info.birthMonth - 1, this.info.birthDay);
        const age = currentDate.getFullYear() - birthDate.getFullYear() - (currentDate.getMonth() < birthDate.getMonth() || (currentDate.getMonth() === birthDate.getMonth() && currentDate.getDate() < birthDate.getDate()) ? 1 : 0);
        const yearsOfExperience = currentDate.getFullYear() - 2017;

        const introLines = [
          `Hello, I'm ${this.info.nickname}.`,
          `I'm ${age} years old.`,
          `I'm ${this.info.nacionality}.`,
          `I'm a ${this.info.occupation} with ${yearsOfExperience} years of experience.`,
          `You can find me on GitHub: <a href="${this.info.github}" target="_blank">${this.info.github}</a>`,
          `And on GitLab: <a href="${this.info.gitlab}" target="_blank">${this.info.gitlab}</a>`,
          `Check out my website: <a href="${this.info.website}" target="_blank">${this.info.website}</a>`
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
      occupation: "JavaScript developer",
      github: "https://github.com/CVFA-Dev",
      gitlab: "https://gitlab.com/CVFA",
      website: "https://cvfa.vercel.app/"
    };

    // Create a Myself object
    const me = new Myself(MyInfo);

    // Introduce myself
    me.introduction();
```
