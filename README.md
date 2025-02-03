# Text

@for (item of menuItems; track item) {
  <div (click)="toggleParentMenu(item)">
    <span>{{ item.title }}</span>
  </div>

  @if (item.isParent && menuState[item.title]) {
    <div class="submenu">
      @for (subItem of item.children; track subItem) {
        <div (click)="toggleChildMenu(subItem, $event)">
          <a >
            <span>{{ subItem.title }}</span>
          </a>
        </div>

        @if (subItem.isParent && menuState[subItem.title]) {
          <div class="submenu">
            @for (subSubItem of subItem.children; track subSubItem) {
              <a >
                <span>{{ subSubItem.title }}</span>
              </a>
            }
          </div>
        }
      }
    </div>
  }
}
<router-outlet></router-outlet>



  menuState: { [key: string]: boolean } = {};

// Function to handle parent menu toggling
toggleParentMenu(item: any) {
  if (item.isParent) {
    // Close all other parent menus
    for (const key in this.menuState) {
      if (key !== item.title) {
        this.menuState[key] = false;
      }
    }
    // Toggle the clicked parent menu
    this.menuState[item.title] = !this.menuState[item.title];
  }
}

// Function to handle child menu toggling
toggleChildMenu(childItem: any, event: Event) {
  if (childItem.isParent) {
    // Prevent the event from bubbling up to the parent
    event.stopPropagation();
    // Toggle the child's submenu
    this.menuState[childItem.title] = !this.menuState[childItem.title];
  }
  // If it's not a parent, routing will handle the navigation
}











export const Menuitems = [
    {
        "title": "Crypto Currencies",
        "isParent": true,
        "children": [
            { "title": "Dashboard", "isParent": false },
            { "title": "Marketcap", "isParent": false },
            { "title": "Currency exchange", "isParent": false },
            { "title": "Buy & Sell", "isParent": false },
            { "title": "Wallet", "isParent": false },
            { "title": "Transactions", "isParent": false }
        ]
    },
    {
        "title": "ECommerce",
        "isParent": true,
        "children": [
            { "title": "Dashboard", "isParent": false },
            { "title": "Products", "isParent": false },
            { "title": "Product Details", "isParent": false },
            { "title": "Cart", "isParent": false },
            { "title": "Wishlist", "isParent": false },
            { "title": "Checkout", "isParent": false },
            { "title": "Orders", "isParent": false },
            { "title": "Add Product", "isParent": false },
            { "title": "Account", "isParent": false }
        ]
    },
    {
        "title": "Landing Page"
    },
    {
        "title": "Apps",
        "isParent": true,
        "children": [
            { "title": "Widgets", "isParent": false },
            { "title": "Sweet Alerts", "isParent": false },
            {
                "title": "Mail",
                "isParent": true,
                "children": [
                    { "title": "Mail-Inbox", "isParent": false },
                    { "title": "View-Mail", "isParent": false },
                    { "title": "Mail-Compose", "isParent": false }
                ]
            },
            {
                "title": "Maps",
                "isParent": true,
                "children": [
                    { "title": "Leaflet Maps", "isParent": false },
                    { "title": "Vector Maps", "isParent": false },
                    { "title": "Google Maps", "isParent": false }
                ]
            },

            {
                "title": "Tables",
                "isParent": true,
                "children": [
                    {
                        "title": "Tables",
                        "isParent": false,
                    },
                    {
                        "title": "Grid JS Tables",
                        "isParent": false,
                    },
                    {
                        "title": "Data Tables",
                        "isParent": false,
                    },
                ]

            },
            {
                "title": "Blog",
                "isParent": true,
                "children": [
                    {
                        "title": "Blog Page",
                        "isParent": false,
                    },
                    {
                        "title": "Bloag Details",
                        "isParent": false,
                    },
                    {
                        "title": "Blog Post",
                        "isParent": false,
                    },
                ]
            },
            {
                "title": "File Manager",
                "isParent": true,
                "children": [
                    {
                        "title": "File Manager",
                        "isParent": false,
                    },
                    {
                        "title": "File Manager List",
                        "isParent": false,
                    },
                    {
                        "title": "File Destails",
                        "isParent": false,
                    },
                ]
            },
        ]
    },
    {
        "title": "icon",
        "isParent": true,
    },
    {
        "title": "Elements",
        "isParent": true,
        "children": [
            { "title": "Accordions & Collapse", "isParent": false },
            { "title": "Alerts", "isParent": false },
            { "title": "Avatars", "isParent": false },
            { "title": "Breadcrumbs", "isParent": false },
            { "title": "Buttons", "isParent": false },
            { "title": "Button Group", "isParent": false },
            { "title": "Badge", "isParent": false },
            { "title": "Dropdowns", "isParent": false },
            { "title": "Images & Figures", "isParent": false },
            { "title": "List Group", "isParent": false },
            { "title": "Navs & Tabs", "isParent": false },
            { "title": "Object Fit", "isParent": false },
            { "title": "Pagination", "isParent": false },
            { "title": "Popovers", "isParent": false },
            { "title": "Progress", "isParent": false },
            { "title": "Spinners", "isParent": false },
            { "title": "Typography", "isParent": false },
            { "title": "Tooltips", "isParent": false },
            { "title": "Toasts", "isParent": false },
            { "title": "Tags", "isParent": false }
        ]
    },
    {
        "title": "Advanced UI",
        "isParent": true,
        "children": [
            { "title": "Carousel", "isParent": false },
            { "title": "Full Calendar", "isParent": false },
            { "title": "Draggable Cards", "isParent": false },
            { "title": "Chat", "isParent": false },
            { "title": "Contacts", "isParent": false },
            { "title": "Cards", "isParent": false },
            { "title": "Timeline", "isParent": false },
            { "title": "Search", "isParent": false },
            { "title": "Userlist", "isParent": false },
            { "title": "Notification", "isParent": false },
            { "title": "Tree-view", "isParent": false },
            { "title": "Modals & Closes", "isParent": false },
            { "title": "Navbar", "isParent": false },
            { "title": "Offcanvas", "isParent": false },
            { "title": "Placeholders", "isParent": false },
            { "title": "ratings", "isParent": false },
            { "title": "Scrollspy", "isParent": false },
            { "title": "Swiper JS", "isParent": false }
        ]
    },
    {
        "title": "Pages",
        "isParent": true,
        "children": [
            { "title": "Profile", "isParent": false },
            { "title": "About Us", "isParent": false },
            { "title": "Settings", "isParent": false },
            { "title": "Invoice", "isParent": false },
            { "title": "Pricing", "isParent": false },
            { "title": "Gallery", "isParent": false },
            { "title": "Notifications List", "isParent": false },
            { "title": "Faqs", "isParent": false },
            { "title": "Success Message", "isParent": false },
            { "title": "Danger Message", "isParent": false },
            { "title": "Warning Message", "isParent": false },
            { "title": "Empty Page", "isParent": false }
        ]
    },
    // Utilities menu
    {
        "title": "Utilities",
        "isParent": true,
        "children": [
            { "title": "Breakpoints", "isParent": false },
            { "title": "Display", "isParent": false },
            { "title": "Borders", "isParent": false },
            { "title": "Colors", "isParent": false },
            { "title": "Flex", "isParent": false },
            { "title": "Columns", "isParent": false },
            { "title": "Gutters", "isParent": false },
            { "title": "Helpers", "isParent": false },
            { "title": "Position", "isParent": false },
            { "title": "More", "isParent": false }
        ]
    },

    // Submenu structure (with nested items)
    {
        "title": "Submenu",
        "isParent": true,
        "children": [
            { "title": "Submenu-01", "isParent": false },
            {
                "title": "Submenu-02",
                "isParent": true,
                "children": [
                    { "title": "Level-01", "isParent": false },
                    { "title": "Level-02", "isParent": false }
                ]
            }
        ]
    }
    ,
    // Authentication menu
    {
        "title": "Authentication",
        "isParent": true,
        "children": [
            { "title": "Sign In", "isParent": false },
            { "title": "Sign Up", "isParent": false },
            { "title": "Forgot Password", "isParent": false },
            { "title": "Reset Password", "isParent": false },
            { "title": "Lockscreen", "isParent": false },
            { "title": "UnderConstruction", "isParent": false },
            { "title": "404 Error", "isParent": false },
            { "title": "500 Error", "isParent": false }
        ]
    },
   // Forms menu (combining both Form images)
{
    "title": "Forms",
    "isParent": true,
    "children": [
      {
        "title": "Form Elements",
        "isParent": true,
        "children": [
          { "title": "Inputs", "isParent": false },
          { "title": "Checks & Radios", "isParent": false },
          { "title": "Input Group", "isParent": false },
          { "title": "Form Select", "isParent": false },
          { "title": "Range Slider", "isParent": false },
          { "title": "Input Masks", "isParent": false },
          { "title": "File Uploads", "isParent": false },
          { "title": "Date,Time Picker", "isParent": false },
          { "title": "Color Picker", "isParent": false }
        ]
      },
      { "title": "Floating Labels", "isParent": false },
      { "title": "Form Layouts", "isParent": false },
      {
        "title": "Form Editor",
        "isParent": true,
        "children": [
          { "title": "Quill Editor", "isParent": false }
        ]
      }
    ]
   },
   
   // Charts menu
   {
    "title": "Charts",
    "isParent": true,
    "children": [
      { "title": "ChartJS", "isParent": false },
      { "title": "Echart", "isParent": false },
      {
        "title": "Apex Charts",
        "isParent": true,
        "children": [
          { "title": "Line Charts", "isParent": false },
          { "title": "Area Charts", "isParent": false },
          { "title": "Column Charts", "isParent": false },
          { "title": "Bar Charts", "isParent": false },
          { "title": "Mixed Charts", "isParent": false },
          { "title": "Range Area Charts", "isParent": false },
          { "title": "Timeline Charts", "isParent": false },
          { "title": "CandleStick Charts", "isParent": false },
          { "title": "Boxplot Charts", "isParent": false },
          { "title": "Bubble Charts", "isParent": false },
          { "title": "Scatter Charts", "isParent": false },
          { "title": "Heatmap Charts", "isParent": false },
          { "title": "Treemap Charts", "isParent": false },
          { "title": "Pie Charts", "isParent": false },
          { "title": "Radialbar Charts", "isParent": false },
          { "title": "Radar Charts", "isParent": false },
          { "title": "Polararea Charts", "isParent": false }
        ]
      }
    ]
   }

    
]
