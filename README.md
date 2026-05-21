<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Receipt - Get Extra Hands</title>
    <!-- Tailwind CSS for modern responsive styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts for premium typography -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc; /* Stripe's cool light gray background */
        }
        /* Printable styling */
        @media print {
            body {
                background-color: white !important;
                padding: 0 !important;
            }
            .no-print {
                display: none !important;
            }
            .print-card {
                box-shadow: none !important;
                border: none !important;
                padding: 0 !important;
                margin: 0 !important;
                max-width: 100% !important;
                width: 100% !important;
            }
        }
    </style>
</head>
<body class="text-slate-800 antialiased min-h-screen py-6 md:py-12 px-4 flex flex-col items-center">

    <!-- Print Action Header (Hidden on print) -->
    <div class="w-full max-w-2xl mb-6 flex justify-end no-print">
        <button onclick="window.print()" class="px-4 py-2.5 text-sm font-semibold text-slate-700 bg-white border border-slate-200 rounded-xl hover:bg-slate-50 hover:border-slate-300 transition-all flex items-center gap-2 shadow-sm">
            <svg class="w-4 h-4 text-slate-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 17h2a2 2 0 002-2v-4a2 2 0 00-2-2H5a2 2 0 00-2 2v4a2 2 0 00-2 2h2m2 4h10a2 2 0 002-2v-4a2 2 0 00-2-2H9a2 2 0 00-2 2v4a2 2 0 002 2zm8-12V5a2 2 0 00-2-2H9a2 2 0 00-2 2v4h10z"></path>
            </svg>
            Print or Save PDF
        </button>
    </div>

    <!-- Main Receipt Card -->
    <div class="w-full max-w-2xl bg-white rounded-2xl border border-slate-200 shadow-[0_4px_12px_rgba(0,0,0,0.02),0_1px_2px_rgba(0,0,0,0.02)] print-card overflow-hidden">
        
        <!-- Receipt Content Container -->
        <div class="p-6 md:p-12">
            
            <!-- Large Centered Logo & Branding Header -->
            <div class="text-center border-b border-slate-100 pb-8">
                <div class="inline-flex items-center justify-center w-28 h-28 md:w-32 md:h-32 bg-white rounded-full mb-4">
                    <img class="w-full h-full object-contain" src="https://res.cloudinary.com/dwmsgnm4p/image/upload/q_auto/f_auto/v1779386601/GEHLOGO_zrvacq.png" alt="Get Extra Hands Logo">
                </div>
                <h1 class="text-2xl font-bold tracking-tight text-slate-900 mt-2">Get Extra Hands</h1>
                <p class="text-xs font-semibold uppercase tracking-wider text-[#635bff] mt-1">Professional Cleaning Services</p>
                
                <!-- Paid Stamp Status Badge -->
                <div class="mt-4 inline-flex items-center gap-1.5 px-4 py-1.5 rounded-full text-sm font-bold bg-emerald-50 text-emerald-700 border border-emerald-100/80">
                    <svg class="w-4 h-4 text-emerald-600" fill="currentColor" viewBox="0 0 20 20">
                        <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"></path>
                    </svg>
                    <span>PAID RECEIPT</span>
                </div>
            </div>

            <!-- Receipt & Client Metadata Info Section -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 py-8 border-b border-slate-100 text-sm">
                
                <!-- Left: Billed To Details -->
                <div class="space-y-1">
                    <span class="text-xs font-semibold tracking-wider text-slate-400 uppercase block mb-2">Billed to</span>
                    <p class="font-semibold text-slate-800">Leslie Islar</p>
                    <p class="text-slate-500">soulcolethebrand@gmail.com</p>
                    <p class="text-slate-500">(301) 602-2697</p>
                    <p class="text-slate-500 whitespace-pre-line mt-1">301 Tingey Street SE
PH28
DC 20003 US</p>
                </div>

                <!-- Right: Receipt Details -->
                <div class="md:text-right space-y-2">
                    <span class="text-xs font-semibold tracking-wider text-slate-400 uppercase block mb-1">Receipt Details</span>
                    <div>
                        <span class="text-slate-400">Receipt No:</span>
                        <span class="font-semibold text-slate-800">#10045</span>
                    </div>
                    <div>
                        <span class="text-slate-400">Payment Date:</span>
                        <span id="payment-date" class="font-medium text-slate-700"></span>
                    </div>
                    
                    <!-- Highlighted Service Day and Time -->
                    <div class="pt-3 border-t border-slate-100 mt-3 text-slate-700 space-y-1">
                        <div>
                            <span class="text-slate-400">Service Date:</span>
                            <span class="font-semibold text-slate-950">6/9/26</span>
                        </div>
                        <div>
                            <span class="text-slate-400">Arrival Window:</span>
                            <span class="font-semibold text-slate-950">7:00 AM - 8:00 AM</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Invoice Line Items Table -->
            <div class="py-6">
                <table class="w-full text-left">
                    <thead>
                        <tr class="border-b border-slate-200 text-xs font-semibold tracking-wider text-slate-400 uppercase">
                            <th class="pb-3 font-semibold">Description</th>
                            <th class="pb-3 text-right font-semibold w-16">Qty</th>
                            <th class="pb-3 text-right font-semibold w-24">Price</th>
                            <th class="pb-3 text-right font-semibold w-24">Amount</th>
                        </tr>
                    </thead>
                    <tbody class="divide-y divide-slate-100 text-sm text-slate-700">
                        <!-- Standard Package -->
                        <tr>
                            <td class="py-4 pr-4">
                                <span class="font-semibold text-slate-900 block">Deep Cleaning Package Base</span>
                                <span class="text-xs text-slate-500 mt-0.5 block max-w-md">
                                    Comprehensive top-to-bottom sanitize of both levels. Includes thorough vacuuming of all rooms/stairs, deep dusting, baseboard detailing, sanitization of 2.5 bathrooms, and hard floor scrubbing/mopping.
                                </span>
                            </td>
                            <td class="py-4 text-right font-medium">1</td>
                            <td class="py-4 text-right font-medium">$270.00</td>
                            <td class="py-4 text-right font-semibold text-slate-900">$270.00</td>
                        </tr>
                        <!-- Inside Oven -->
                        <tr>
                            <td class="py-4 pr-4">
                                <span class="font-semibold text-slate-900 block">Add-on: Inside Oven Deep Clean</span>
                                <span class="text-xs text-slate-500 mt-0.5 block max-w-lg">
                                    Thorough interior oven degreasing, baking rack scrub, window scrape, and polishing.
                                </span>
                            </td>
                            <td class="py-4 text-right font-medium">1</td>
                            <td class="py-4 text-right font-medium">$60.00</td>
                            <td class="py-4 text-right font-semibold text-slate-900">$60.00</td>
                        </tr>
                        <!-- Inside Fridge -->
                        <tr>
                            <td class="py-4 pr-4">
                                <span class="font-semibold text-slate-900 block">Add-on: Inside Refrigerator Deep Clean</span>
                                <span class="text-xs text-slate-500 mt-0.5 block max-w-lg">
                                    Detailed sanitization of interior shelves, door guards, drawers, and cooling components.
                                </span>
                            </td>
                            <td class="py-4 text-right font-medium">1</td>
                            <td class="py-4 text-right font-medium">$60.00</td>
                            <td class="py-4 text-right font-semibold text-slate-900">$60.00</td>
                        </tr>
                    </tbody>
                </table>
            </div>

            <!-- Financial Totals Block -->
            <div class="flex justify-end border-t border-slate-100 pt-6">
                <div class="w-full md:w-80 space-y-3 text-sm">
                    <div class="flex justify-between text-slate-500">
                        <span>Subtotal</span>
                        <span class="font-medium">$390.00</span>
                    </div>
                    <div class="flex justify-between text-emerald-600 font-medium">
                        <span>Promo Discount (maypeace)</span>
                        <span>-$50.00</span>
                    </div>
                    <div class="flex justify-between text-slate-500">
                        <span>Tax (0%)</span>
                        <span class="font-medium">$0.00</span>
                    </div>
                    <div class="flex justify-between text-slate-900 pt-3 border-t border-slate-100">
                        <span class="font-bold text-slate-900 text-base">Total Paid</span>
                        <span class="font-bold text-xl text-emerald-600" id="final-total">$340.00</span>
                    </div>
                </div>
            </div>

            <!-- Professional Footer -->
            <div class="border-t border-slate-100 mt-12 pt-6">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 text-xs text-slate-500">
                    <div>
                        <h4 class="font-bold uppercase tracking-wider text-slate-400 mb-2">Important Reminders</h4>
                        <p class="leading-relaxed">
                            Thank you for your payment! Please lookout for text/email reminders as your scheduled service date of <strong>6/9/26</strong> approaches.
                        </p>
                    </div>
                    <div>
                        <h4 class="font-bold uppercase tracking-wider text-slate-400 mb-2">Questions? Contact Us</h4>
                        <p class="leading-relaxed">
                            If you have any questions, please reach out to us:
                        </p>
                        <div class="mt-2 space-y-1 font-medium text-slate-700">
                            <div>Email: <a href="mailto:team@getextrahands.com" class="text-[#635bff] hover:underline">team@getextrahands.com</a></div>
                            <div>Phone: <a href="tel:3019660803" class="text-[#635bff] hover:underline">301-966-0803</a></div>
                        </div>
                    </div>
                </div>
                
                <!-- Payment badge detail -->
                <div class="mt-8 pt-4 border-t border-slate-100/60 flex flex-wrap justify-between items-center gap-4 text-xs text-slate-400">
                    <span class="flex items-center gap-1.5">
                        <svg class="w-4 h-4 text-emerald-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"></path></svg>
                        Secure Digital Payment Completed
                    </span>
                    <span>Get Extra Hands LLC &bull; Reference Code: 240517 6333 GEH/Getextrahands</span>
                </div>
            </div>

        </div>
    </div>

    <script>
        // Set dates automatically
        document.addEventListener('DOMContentLoaded', () => {
            const today = new Date();
            const formattedToday = today.toLocaleDateString('en-US', {
                year: 'numeric',
                month: 'long',
                day: 'numeric'
            });
            document.getElementById('payment-date').innerText = formattedToday;
        });
    </script>
</body>
</html>
