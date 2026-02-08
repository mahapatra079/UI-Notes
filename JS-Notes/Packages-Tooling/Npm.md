Npm vs Npx :-

        npm - Node Package Manager ; used to install packages

        Used For :-
                    
                    * install pacckages

                    * Manage node_modules (npm i)

                    * Maintain the package.json

                    * Run Scripts  - npm run build
                                        npm start


        Example : npm install react

                    => Installs React

                    Saves it in node_modules

                    Updates package.json


        npx - Node Package eXecute ; Used to execute a package without installing it globally.

        Used For :- 

                    * Run CLI tools directly
                        
                        A Command-Line Interface (CLI) is a text-based user interface used to interact with software
                        and operating systems by typing commands

                        The CLI is the central entry point for frontend development. Its primary function is to transpile and bundle your code for development.

                    * Avoid global installs

                    * Run one-time commands 

        Example -  npx create-react-app myApp

                        => Downloads create-react-app

                        Executes it

                        Deletes it after use (if not cached)

Note:  
        Use npm for dependencies

        Use npx for tools like:

            create-react-app

            vite

            eslint

            prettier

2) Yarn vs Pnpm :-

                    Yarn - alternative to npm
                    
                    how it works

                            * use yarn.lock

                            * Parallel install

                            * Deterministic dependency tree