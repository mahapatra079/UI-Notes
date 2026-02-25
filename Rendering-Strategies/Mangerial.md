# Managerial Scenarios

1) what is code splitting ?

        Code splitting is a performance optimization technique where a large JavaScript bundle 
        is split into smaller chunks that are loaded only when required.

        Instead of loading the entire application at once, we load specific modules or routes 
        dynamically on-demand.

        Example: If a user visits the homepage, they don't need admin dashboard code loaded yet.

        Implementation:
        - React: React.lazy() and Suspense
        - Vue: Dynamic imports in routes () => import('./Component.vue')

        Benefits:
        - Reduces initial bundle size (e.g., 2MB → 500KB)
        - Faster initial load time
        - Better performance, especially on slow networks

     Tools to analyze: Webpack Bundle Analyzer, Lighthouse

2) Junior developer struggling - what will you do?

     I would understand the root cause of the issue, guide them step-by-step, and encourage learning through pair programming and debugging.
     I believe in supporting juniors while ensuring project deadlines are met.


3) How will you manage roles?
    
    I manage roles by first understanding each team member’s strengths, experience, and interests. I assign responsibilities based on project requirements and ensure clear ownership to avoid confusion.
    I believe in giving ownership while avoiding micromanagement. I also balance workload so that juniors get learning opportunities while seniors handle critical parts like architecture and code reviews. Regular standups and code reviews help me monitor progress and support the team if needed.




    Traffic Light 
              
          import { useEffect, useState } from "react";


            export default function TrafficSignals() {
                const [curentSignal, setCurrentSignal] = useState('red')

                useEffect(() =>{
                    let timer:number;
                    if(curentSignal === 'red'){
                        timer = setTimeout(() => setCurrentSignal('green'), 2000);
                    } else if(curentSignal === 'green'){
                        timer = setTimeout(() => setCurrentSignal('yellow'), 3000);
                    } else if(curentSignal === 'yellow'){
                        timer = setTimeout(() => setCurrentSignal('red'), 4000);
                    }

                    return () => clearTimeout(timer);
                },[curentSignal])
            return(
                <div className="flex flex-col items-center justify-center h-screen">
                    <div className={`w-24 h-24 rounded-full mb-4 ${curentSignal === 'red' ? 'bg-red-500' : 'bg-gray-300'}`}></div>
                    <div className={`w-24 h-24 rounded-full mb-4 ${curentSignal === 'green' ? 'bg-green-500' : 'bg-gray-300'}`}></div>
                    <div className={`w-24 h-24 rounded-full mb-4 ${curentSignal === 'yellow' ? 'bg-yellow-500' : 'bg-gray-300'}`}></div>
                </div>
            )
            }

 