<template>
    <div class="max-w-7xl mx-auto grid grid-cols-2 gap-4">
        <div class="main-left">
            <div class="p-12 bg-white border border-gray-200 rounded-lg">
                <h1 class="mb-6 text-2xl">Sign Up</h1>
                <p class="mb-6 text text-gray-500">
                    Join Goiaba Social Network for exclusive perks and endless opportunities! Connect with like-minded individuals, engage in lively discussions, and discover exciting events. Whether you're seeking inspiration or looking to expand your network, our platform offers a dynamic space for you to express yourself freely. 
                </p>
                <p class="font-bold">
                    Already have an account? 
                    <RouterLink to="/login" class="underline">Log In</RouterLink>
                </p>
            </div>
        </div>
        <div class="main-right">
            <div class="p-12 bg-white border border-gray-200 rounded-lg">
                <form class="space-y-6">
                    <div>
                        <label>Name</label><br>
                        <input type="text" placeholder="Your full name" class="w-full mt-2 py-4 px-6 border border-gray-200 rounded-lg">
                    </div>

                    <div>
                        <label>E-mail</label><br>
                        <input type="email" placeholder="Your e-mail address" class="w-full mt-2 py-4 px-6 border border-gray-200 rounded-lg">
                    </div>

                    <div>
                        <label>Password</label><br>
                        <input type="password" placeholder="Your password" class="w-full mt-2 py-4 px-6 border border-gray-200 rounded-lg">
                    </div>

                    <div>
                        <label>Repeat password</label><br>
                        <input type="password" placeholder="Repeat your password" class="w-full mt-2 py-4 px-6 border border-gray-200 rounded-lg">
                    </div>

                    <div>
                        <button class="py-4 px-6 bg-pink-600 text-white">Sign up</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>