## 1. Structure
- **/apps**
  - **/api** - NestJS project, the BackEnd API of the application.
  - **/ui** - ReactJS project, the FrontEnd of the application. 
- **/libs** - common shared libraries (interfaces, models, utilities) used by both BE and FE
- **/tools** - custom utility functions for the CLI commands
## 2. Get Started
### Local development
Run ```docker compose up``` in the root folder. Your apps will start in parallel, including any dependencies. You can then access them, the FE at [localhost:3000](http://localhost:3000) and the BE at [localhost:8080](http://localhost:8080). Hot reload will be enabled for both apps.

Both apps use Typescript and linting rules, configured in ```.eslintcrc.json```

For unit tests, the default preset is Jest library.

Useful tips:
- use ```workspace.json``` to configure additional cli commands
- it is reccommended to install nx globally, to avoid prepending npx to each command. To do so, run: ```npm i -g nx```
- to generate FE resources, use the built in nx [React Generator](https://nx.dev/latest/react/react/overview)
  - eg for a new component generation: ```nx generate component <component-name> --project=ui```
- to generate BE resources, use the build in nx [NestJS Generator](https://nx.dev/latest/react/nest/overview)
  - note: the React generator is the default generator
  - to use the NestJS generator, you need to explicitly pass it to the command, eg: ```nx generate @nrwl/nest:controller --name=<controller-name> --project=api```
- the React app is styled using Styled Components
- when running the app locally, it automatically uses a proxy for localhost:8080 as /api. We can leverage ui/environments/environment.ts to determine if the app is run locally, and decide upon using an env var to point to the BE url for other environments

### BE Docker Image
Build the image using ```nx run api:docker``` and ```nx run api:deploy:production```, this will generate the docker image you can then run using ```docker run -it --rm -p 8080:8080 lem\api-prod```
### FE Docker Image
Build the image using ```nx run ui:deploy``` and then run the resulting image with ```docker run -it --rm -p 3000:3000 lem\ui```