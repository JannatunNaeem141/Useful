# Password Strength Checker
Sometimes we need to validate the user password and show the weak or strong indicator or texts. Let's make a strength checker where we will check 5 conditions like "At least 8 characters long, 1 number, 1 lowercase letter, 1 uppercase letter & 1 special character". 

### Technologies
- HTML
- TailwindCSS
- JavaScript

### HTML Code:
```jsx
  <div class="dark:bg-[#16192E] border border-[#ECEFF3] dark:border-[#23283F] rounded-lg commonBoxShadow">
      <div class="bg-[#fafafa] dark:bg-[#1C2037] px-4 py-2 rounded-t-lg">
          <h3 class="font-medium text-[#615E83] dark:text-[#D9DBE4]">Change Password</h3>
      </div>
      <form id="passwordForm" class="flex flex-col gap-7 px-4 py-5">
          <div>
              <input
                  type="password"
                  id="passwordInput"
                  placeholder="New Password"
                  class="text-[#989CAE] dark:text-[#666D80] text-sm border border-[#ECEFF3] dark:border-[#23283F] bg-white dark:bg-[#15172B] rounded-lg p-3 w-full outline-none"
                  oninput="checkPasswordStrength()"
              />
              <div id="strengthIndicator" class="flex items-center justify-between mt-2 mx-2">
                  <div class="flex items-center gap-1">
                      <div id="weakIndicator" class="bg-[#FB5252] w-5 h-1 rounded-full hidden"></div>
                      <div id="mediumIndicator" class="bg-[#FCA120] w-5 h-1 rounded-full hidden"></div>
                      <div id="strongIndicator" class="bg-[#2BC48A] w-5 h-1 rounded-full hidden"></div>
                  </div>
                  <div class="flex items-center gap-1">
                      <span id="strengthText" class="text-[#989CAE] text-xs"></span>
                      <span class="cursor-pointer" title="At least 8 characters long, 1 number, 1 lowercase letter, 1 uppercase letter & 1 special character">
                          <svg xmlns="http://www.w3.org/2000/svg" width="15" height="14" viewBox="0 0 15 14" fill="none">
                              <path d="M7.375 4.875H7.38208M1 7C1 7.83718 1.16489 8.66616 1.48527 9.43961C1.80564 10.2131 2.27522 10.9158 2.86719 11.5078C3.45917 12.0998 4.16194 12.5694 4.93539 12.8897C5.70884 13.2101 6.53782 13.375 7.375 13.375C8.21218 13.375 9.04116 13.2101 9.81461 12.8897C10.5881 12.5694 11.2908 12.0998 11.8828 11.5078C12.4748 10.9158 12.9444 10.2131 13.2647 9.43961C13.5851 8.66616 13.75 7.83718 13.75 7C13.75 5.30924 13.0783 3.68774 11.8828 2.49219C10.6873 1.29665 9.06575 0.625 7.375 0.625C5.68424 0.625 4.06274 1.29665 2.86719 2.49219C1.67165 3.68774 1 5.30924 1 7Z" stroke="#adb0c1" stroke-linecap="round" stroke-linejoin="round"/>
                              <path d="M6.66699 7H7.37533V9.83333H8.08366" stroke="#adb0c1" stroke-linecap="round" stroke-linejoin="round"/>
                          </svg>
                      </span>
                  </div>
              </div>
          </div>
          <input
              type="password"
              placeholder="Retype New Password"
              class="text-[#989CAE] dark:text-[#666D80] text-sm border border-[#ECEFF3] dark:border-[#23283F] bg-white dark:bg-[#15172B] rounded-lg p-3 w-full outline-none"
          />
          <div class="flex">
              <input type="submit" value="Change Password" class="bg-[#0075FF] text-white text-sm rounded-lg py-2 px-3 cursor-pointer active:scale-95 transition-all duration-150" />
          </div>
      </form>
  </div>
```
