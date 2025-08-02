import plistlib
import time

FILE_PATH = "/private/var/db/os_eligibility/eligibility.plist"
INTERVAL_SECONDS = 3  # Change as needed

DESIRED_SETTINGS = {
    "os_eligibility_answer_t": 4,
    "status": {
        "OS_ELIGIBILITY_INPUT_COUNTRY_BILLING": 3,
        "OS_ELIGIBILITY_INPUT_COUNTRY_LOCATION": 3,
    }
}

def check_and_update():
    updated = False
    with open(FILE_PATH, "rb") as file:
        plist_data = plistlib.load(file)

    iron = plist_data.get("OS_ELIGIBILITY_DOMAIN_IRON")
    if not iron:
        print("OS_ELIGIBILITY_DOMAIN_IRON not found!")
        return

    if iron.get("os_eligibility_answer_t") != DESIRED_SETTINGS["os_eligibility_answer_t"]:
        iron["os_eligibility_answer_t"] = DESIRED_SETTINGS["os_eligibility_answer_t"]
        updated = True

    status = iron.get("status")
    if isinstance(status, dict):
        for key, desired_value in DESIRED_SETTINGS["status"].items():
            if status.get(key) != desired_value:
                status[key] = desired_value
                updated = True

    if updated:
        with open(FILE_PATH, "wb") as file:
            plistlib.dump(plist_data, file)
        print("Plist has been updated!")
    else:
        print("Values are already correct. No update needed.")

def main():
    while True:
        try:
            check_and_update()
        except Exception as e:
            print(f"Error: {e}")
        time.sleep(INTERVAL_SECONDS)

if __name__ == "__main__":
    main()
