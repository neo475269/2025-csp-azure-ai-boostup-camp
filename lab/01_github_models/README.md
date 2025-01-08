# Github Models

#### Description   
In this lab you are going to show how you can use GitHub models quickly to create an insurance report from a video.

#### Required access and products
- GitHub account

#### Running the notebook
- Start a codespace from the repository
- browse to the notebook in session-delivery-resources/github-models/insurance-assistant.ipynb
- Run the notebook (select the Python 3.11 Kernel)

## Demo walkthrough

- [Backup video recording](https://aka.ms/AArvo1o)
- [Demo files](/lab/1-github-models/)

### Part 1 - Playground & System message
- Go to GitHub.com and login with your github account
- Navigate to the [GitHub Models](https://gh.io/models)
- Click on playground    
    - Select GPT-4o Mini
    - click Compare and select another model
    - System Prompt: You are a grumpy assistant, only answering questions about the rubber ducks
    - In the user message type: "Hello" and see how they respond differently


### Part 2 - Running Psuedo Prompt on GitHub Model Playground and convert to Python code
![PsuedoPrompt](media/PsuedoPrompt.png)
- Navigate to a model in the [GitHub Models](https://gh.io/models)
- Click on playground    
    - Select GPT-4o
    - System Prompt:
        ```
        // Program: MinimumSalary
        minimumSalary = $100,000

        constraint SalaryFloor {
            for each employee {
                employee.salary >= $minimumSalary;
                onChange {
                    emit({ constraint: 'SalaryFloor', employee: employee, raise: constraintDifference })
                }
            }
        }

        joe = employee({ name: 'joe', salary: $110,000 })

        minimumSalary = $120,000;

        log(joe.salary) // Output: 120,000
        
    - In the user message type
        ```
        run(MinimumSalary) |> list(events) |> log:format=json

    - Click *Code* to check the available languages and libraries to work with GitHub Models
    - Follow instruction to create the token and copy the token
    

- Open repo in codespace
    - Rename `.env.example` to `.env` and update the token to **GITHUB_TOKEN**
    - Open "02_ai_inference_sdk.ipynb"
    - Run the cells which they are using the same System Prompt and User Message as above with Azure AI Inference SDK

### Part 3 - Azure AI Inference SDK
- Navigate to a model in the [GitHub Models](https://gh.io/models)
- Click on: Get Started (Discuss the different options)
- Open "03_insurance_assistant.ipynb" in the running codespace
- Run and discuss the cells
    - 1 - Extract 14 frames from the video
    - 2 - Send the frames + prompt to the model using the Azure AI Inference SDK
    - 3 - Discuss the models output
